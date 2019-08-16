---
title: CInvalidArgException (clase)
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: d2df9b482fe95ad0a13a85a51037a4cbbc28d057
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392626"
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException (clase)

Esta clase representa una condición de excepción de argumento no válido.

## <a name="syntax"></a>Sintaxis

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|El constructor.|

## <a name="remarks"></a>Comentarios

Un `CInvalidArgException` objeto representa una condición de excepción de argumento no válido.

Para obtener más información sobre el control de excepciones, vea el [clase CException](../../mfc/reference/cexception-class.md) tema y [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException

El constructor.

```
CInvalidArgException();
```

### <a name="remarks"></a>Comentarios

No utilice este constructor directamente; Llame a la función global **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException (clase)](../../mfc/reference/csimpleexception-class.md)
