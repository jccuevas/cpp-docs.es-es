---
title: CMemoryException (clase)
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 375b4227a25ae4c18cfd263eff4c3ec13f1304e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370009"
---
# <a name="cmemoryexception-class"></a>CMemoryException (clase)

Representa una condición de excepción de memoria insuficiente.

## <a name="syntax"></a>Sintaxis

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Construye un objeto `CMemoryException`.|

## <a name="remarks"></a>Observaciones

No es necesaria ni posible ninguna otra cualificación. Las excepciones de memoria se producen automáticamente mediante **new**. Si escribe sus propias `malloc`funciones de memoria, utilizando , por ejemplo, entonces usted es responsable de producir excepciones de memoria.

Para obtener `CMemoryException`más información sobre , vea el artículo Control de [excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException::CMemoryException

Construye un objeto `CMemoryException`.

```
CMemoryException();
```

### <a name="remarks"></a>Observaciones

No utilice este constructor directamente, sino que llame a la función global [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). esta función global puede tener éxito en una situación de memoria insuficiente porque construye el objeto de excepción en la memoria asignada anteriormente. Para obtener más información sobre el procesamiento de excepciones, consulte las [excepciones](../exception-handling-in-mfc.md)de artículo .

## <a name="see-also"></a>Consulte también

[Clase CException](cexception-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)
