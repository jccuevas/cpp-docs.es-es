---
title: Clases compartidas por MFC y ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: 5376a87aac2b82615cd48f80e0e95208b8132bf0
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750486"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Clases compartidas por MFC y ATL

En la tabla siguiente se enumera las clases que se comparten entre MFC y ATL.

|Clase|Descripción|Archivo de encabezado|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Proporciona métodos para administrar los valores de fecha y hora asociados a un archivo.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Proporciona métodos para administrar asociados a un archivo de valores de hora y fecha relativa.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Representa un objeto de cadena con un búfer de caracteres fijos.|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|proporciona compatibilidad con mapas de bits mejorada, incluida la capacidad para cargar y guardar imágenes en los formatos GIF, JPEG, BMP y gráficos de red portátiles (PNG).|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Encapsula el tipo de datos de fecha utilizado en la automatización OLE.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Representa un tiempo relativo, un intervalo de tiempo.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Una clase similar a la Windows [punto](/windows/desktop/api/windef/ns-windef-tagpoint) estructura que también incluye funciones de miembro para manipular `CPoint` y `POINT` estructuras.|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Una clase similar a un Windows [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura que también incluye funciones de miembro para manipular `CRect` objetos y Windows `RECT` estructuras.|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Representa un `CSimpleStringT` objeto.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Una clase similar a la Windows [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) estructura que implementa una coordenada relativa o una posición.|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Proporciona la limpieza de recursos automática para `GetBuffer` y `ReleaseBuffer` llama en una existente `CStringT` objeto.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Representa los datos de un objeto de cadena.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Representa un `CStringT` objeto.|atlstr.h CStringT.h (depende de MFC) (independientes de MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Representa una fecha y hora absoluta.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Un período de tiempo, que se almacena internamente como el número de segundos en el intervalo de tiempo.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Representa la interfaz para un `CStringT` Administrador de memoria.|atlsimpstr.h|

## <a name="see-also"></a>Vea también

[Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
