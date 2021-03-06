---
title: KSPROPERTY\_MAP\_CAPTURE\_HANDLE\_TO\_VRAM\_ADDRESS
description: The KSPROPERTY\_MAP\_CAPTURE\_HANDLE\_TO\_VRAM\_ADDRESS property returns the capture driver's mapping of a VRAM surface handle to a VRAM physical address.To use VRAM transport, a capture minidriver must support this property.
ms.assetid: 071c9152-12f9-4ec1-80d7-6b42fce51bbb
keywords: ["KSPROPERTY_MAP_CAPTURE_HANDLE_TO_VRAM_ADDRESS Streaming Media Devices"]
topic_type:
- apiref
api_name:
- KSPROPERTY_MAP_CAPTURE_HANDLE_TO_VRAM_ADDRESS
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.author: windowsdriverdev
ms.date: 11/28/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.localizationpriority: medium
---

# KSPROPERTY\_MAP\_CAPTURE\_HANDLE\_TO\_VRAM\_ADDRESS


The KSPROPERTY\_MAP\_CAPTURE\_HANDLE\_TO\_VRAM\_ADDRESS property returns the capture driver's mapping of a VRAM surface handle to a VRAM physical address.

To use VRAM transport, a capture minidriver must support this property.

### <span id="Usage_Summary_Table"></span><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>Usage Summary Table

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Get</th>
<th>Set</th>
<th>Target</th>
<th>Property descriptor type</th>
<th>Property value type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>Pin</p></td>
<td><p>[<strong>VRAM_SURFACE_INFO_PROPERTY_S</strong>](https://msdn.microsoft.com/library/windows/hardware/ff568785)</p></td>
<td><p>DWORD</p></td>
</tr>
</tbody>
</table>

 

### <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value

A KSPROPERTY\_MAP\_CAPTURE\_HANDLE\_TO\_VRAM\_ADDRESS returns STATUS\_SUCCESS to indicate that it has completed successfully. Otherwise, the request returns an appropriate error code.

Remarks
-------

The capture driver should perform the mapping in the handler for this property.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Header</p></td>
<td>Ksmedia.h (include Ksmedia.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**KSPROPERTY**](https://msdn.microsoft.com/library/windows/hardware/ff564262)

 

 






