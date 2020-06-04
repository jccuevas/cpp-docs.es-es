---
title: Clase CInvalidArgException
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: b28b6e84043b85a8117694a67ff5fff13e7c786b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372376"
---
# <a name="cinvalidargexception-class"></a>Clase CInvalidArgException

Esta clase representa una condición de excepción de argumento no válido.

## <a name="syntax"></a>Sintaxis

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|El constructor.|

## <a name="remarks"></a>Observaciones

Un `CInvalidArgException` objeto representa una condición de excepción de argumento no válido.

Para obtener más información sobre el control de [excepciones,](../../mfc/reference/cexception-class.md) vea el tema Clase CException y El control de [excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException

El constructor.

```
CInvalidArgException();
```

### <a name="remarks"></a>Observaciones

No utilice este constructor directamente; llame a la función global **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CSimpleException](../../mfc/reference/csimpleexception-class.md)
