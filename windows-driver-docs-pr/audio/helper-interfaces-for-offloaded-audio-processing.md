---
Description: 'This topic presents the helper interfaces that Microsoft has added to its audio port-class driver (PortCls), to simplify the implementation of drivers that support offloaded-audio processing.'
MS-HAID: 'audio.helper\_interfaces\_for\_offloaded\_audio\_processing'
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Helper Interfaces for Offloaded Audio Processing
---

# Helper Interfaces for Offloaded Audio Processing


This topic presents the helper interfaces that Microsoft has added to its audio port-class driver (PortCls), to simplify the implementation of drivers that support offloaded-audio processing.

When you develop your WaveRT miniport driver that will work with an audio adapter that is capable of processing hardware-offloaded audio streams, your miniport driver works with PortCls to stream and/or process audio data.

PortCls has been updated to handle all the offload-related kernel streaming (KS) properties, and that is what makes it simple to develop a WaveRT miniport driver to expose support for processing hardware-offloaded audio streams. As a result of the updates, PortCls only calls the underlying miniport driver for hardware and/or driver-specific operations via two newly defined interfaces:

-   [**IMiniportAudioEngineNode**](audio.iminiportaudioenginenode)

-   [**IMiniportStreamAudioEngineNode**](audio.iminiportstreamaudioenginenode)

You must develop two classes to work with these interfaces, one for each interface.

## <span id="Working_with_IMiniportAudioEngineNode"></span><span id="working_with_iminiportaudioenginenode"></span><span id="WORKING_WITH_IMINIPORTAUDIOENGINENODE"></span>Working with IMiniportAudioEngineNode


The class that you develop to work with **IMiniportAudioEngineNode**, must also inherit from [IMiniportWaveRT](audio.iminiportwavert). The methods defined in **IMiniportAudioEngineNode** allow your driver to use KS properties that access the audio engine via a KS filter handle. The class/interface hierarchy is as follows:

![the custom wavert miniport class inherits from iminiportwavert and from iminiportaudioenginenode.](images/offload-class-hier1.png)

So if, for example, you develop a class called CYourMiniportWaveRT, then as you can see from the preceding diagram, CYourMiniportWaveRT must implement all the methods (shown as Operations) defined for the two parent interfaces.

A skeletal template for such a class would contain the following code:

```ManagedCPlusPlus
class CMiniportWaveRT : 
    public IMiniportWaveRT,
    public IMiniportAudioEngineNode,
    public CUnknown
{
...

    IMP_IMiniportWaveRT;
    IMP_IMiniportAudioEngineNode;
...

};
```

The *Portcls.h* header file defines these interfaces.

## <span id="Working_with_IMiniportStreamAudioEngineNode"></span><span id="working_with_iminiportstreamaudioenginenode"></span><span id="WORKING_WITH_IMINIPORTSTREAMAUDIOENGINENODE"></span>Working with IMiniportStreamAudioEngineNode


The class that you develop to work with the second interface, **IMiniportStreamAudioEngineNode**, must also inherit from [IMiniportWaveRTStreamNotification](audio.iminiportwavertstreamnotification). The methods defined in **IMiniportStreamAudioEngineNode** allow your driver to use KS properties that access the audio engine via a pin instance handle. The class/interface hierarchy is as follows:

![the custom wavert stream miniport class inherits from iminiportwavertstreamnotification and from iminiportstreamaudioenginenode.](images/offload-class-hier2.png)

So if, for example, you develop a class called CYourMiniportWaveRTStream, then as you can see from the preceding diagram, CYourMiniportWaveRTStream must implement all the methods defined for the two parent interfaces.

A skeletal template for such a class would contain the following code:

```ManagedCPlusPlus
class CMiniportWaveRTStream : 
    public IMiniportWaveRTStreamNotification,
    public IMiniportStreamAudioEngineNode,
    public CUnknown
{
...
    IMP_IMiniportWaveRTStream;
    IMP_IMiniportWaveRTStreamNotification;
    IMP_IMiniportStreamAudioEngineNode;
...

};
```

The *Portcls.h* header file defines these interfaces. And for more information about how to develop a driver that can handle hardware-offloaded audio streams, see [Driver Implementation Details](driver-implementation-details.md).

 

 


--------------------
[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[audio\audio]:%20Helper%20Interfaces%20for%20Offloaded%20Audio%20Processing%20%20RELEASE:%20%287/14/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/en-us/default.aspx. "Send comments about this topic to Microsoft")

