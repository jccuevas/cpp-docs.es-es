---
title: CNotSupportedException (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b52151dba90c0cfd0ed834e2ef351838d598eb90
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068807"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException (clase)

Representa una excepción que es el resultado de una solicitud de una característica no compatible.

## <a name="syntax"></a>Sintaxis

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Construye un objeto `CNotSupportedException`.|

## <a name="remarks"></a>Comentarios

Calificación adicional no es necesaria ni posible.

Para obtener más información sobre el uso de `CNotSupportedException`, consulte el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException

Construye un objeto `CNotSupportedException`.

```
CNotSupportedException();
```

### <a name="remarks"></a>Comentarios

No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). Para obtener más información sobre el procesamiento de excepciones, vea el artículo [control de excepciones en MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Vea también

[CException (clase)](cexception-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)

