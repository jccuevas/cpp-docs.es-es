---
title: Clase CNotSupportedException
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: b859b939baef018e69b245e597eea90e608253ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363193"
---
# <a name="cnotsupportedexception-class"></a>Clase CNotSupportedException

Representa una excepción que es el resultado de una solicitud de una característica no compatible.

## <a name="syntax"></a>Sintaxis

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Construye un objeto `CNotSupportedException`.|

## <a name="remarks"></a>Observaciones

No es necesaria ni posible ninguna otra cualificación.

Para obtener más `CNotSupportedException`información sobre el uso , vea el artículo Control de [excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException

Construye un objeto `CNotSupportedException`.

```
CNotSupportedException();
```

### <a name="remarks"></a>Observaciones

No utilice este constructor directamente, sino que llame a la función global [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). Para obtener más información sobre el procesamiento de excepciones, vea el artículo Control de [excepciones en MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Clase CException](cexception-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)
