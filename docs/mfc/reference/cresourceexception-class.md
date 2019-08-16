---
title: CResourceException (clase)
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: b29112b4901a1fecac37aa7ae61496e874959370
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372203"
---
# <a name="cresourceexception-class"></a>CResourceException (clase)

Se genera cuando Windows no puede encontrar o asignar un recurso solicitado.

## <a name="syntax"></a>Sintaxis

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Construye un objeto `CResourceException`.|

## <a name="remarks"></a>Comentarios

Calificación adicional no es necesaria ni posible.

Para obtener más información sobre el uso de `CResourceException`, consulte el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

Construye un objeto `CResourceException`.

```
CResourceException();
```

### <a name="remarks"></a>Comentarios

No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Para obtener más información sobre las excepciones, vea el artículo [control de excepciones en MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Vea también

[CException (clase)](cexception-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)
