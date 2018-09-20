---
title: CInvalidArgException (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
dev_langs:
- C++
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cff0727f1d194982ad76d24b0a91875448ea45c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389818"
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
