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
ms.openlocfilehash: aa7fd6e2caa15a256cec2eae5ede6c6e47cd1518
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632701"
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

