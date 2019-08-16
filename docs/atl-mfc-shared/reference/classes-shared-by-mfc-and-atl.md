---
title: Clases compartidas por MFC y ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491461"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Clases compartidas por MFC y ATL

En la tabla siguiente se enumeran las clases compartidas entre MFC y ATL.

|Clase|DESCRIPCIÓN|Archivo de encabezado|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Proporciona métodos para administrar los valores de fecha y hora asociados a un archivo.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Proporciona métodos para administrar valores de fecha y hora relativos asociados a un archivo.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Representa un objeto de cadena con un búfer de caracteres fijo.|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Proporciona compatibilidad mejorada con mapas de bits, incluida la capacidad de cargar y guardar imágenes en formatos JPEG, GIF, BMP y Portable Network Graphics (PNG).|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Encapsula el tipo de datos de fecha utilizado en la automatización OLE.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Representa una hora relativa, un intervalo de tiempo.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Clase similar a la estructura de [punto](/windows/win32/api/windef/ns-windef-point) de Windows que también incluye funciones miembro para manipular `CPoint` y `POINT` estructuras.|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Clase similar a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) de Windows que también incluye funciones miembro para manipular `CRect` objetos y estructuras de Windows. `RECT`|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Representa un `CSimpleStringT` objeto.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Clase similar a la estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) de Windows, que implementa una coordenada relativa o una posición.|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Proporciona limpieza de recursos automática `GetBuffer` para `ReleaseBuffer` y llama a en `CStringT` un objeto existente.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Representa los datos de un objeto de cadena.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Representa un `CStringT` objeto.|CStringT. h (dependiente de MFC) atlstr. h (independiente de MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Representa una fecha y hora absolutas.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Cantidad de tiempo, que se almacena internamente como el número de segundos del intervalo de tiempo.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Representa la interfaz para un `CStringT` administrador de memoria.|atlsimpstr.h|

## <a name="see-also"></a>Vea también

[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
