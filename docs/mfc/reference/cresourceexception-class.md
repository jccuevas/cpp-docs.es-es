---
title: Clase CResourceException
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: 557bfe1cc41c3dda65bd95d7d687820c0b9862b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368326"
---
# <a name="cresourceexception-class"></a>Clase CResourceException

Se genera cuando Windows no puede encontrar o asignar un recurso solicitado.

## <a name="syntax"></a>Sintaxis

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Construye un objeto `CResourceException`.|

## <a name="remarks"></a>Observaciones

No es necesaria ni posible ninguna otra cualificación.

Para obtener más `CResourceException`información sobre el uso , vea el artículo Control de [excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a>CResourceException::CResourceException

Construye un objeto `CResourceException`.

```
CResourceException();
```

### <a name="remarks"></a>Observaciones

No utilice este constructor directamente, sino que llame a la función global [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Para obtener más información acerca de las excepciones, vea el artículo Control de [excepciones en MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Clase CException](cexception-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)
