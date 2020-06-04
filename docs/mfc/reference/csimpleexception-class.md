---
title: Clase CSimpleException
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: eb94ba9e3d26b3cd910f23c3d4abb29d3b8b1cd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318360"
---
# <a name="csimpleexception-class"></a>Clase CSimpleException

Esta clase es una clase base para excepciones MFC de recursos críticos.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|Proporciona texto sobre un error que se ha producido.|

## <a name="remarks"></a>Observaciones

`CSimpleException`es la clase base para las excepciones MFC críticas para los recursos y controla la propiedad y la inicialización de un mensaje de error. Las clases `CSimpleException` siguientes utilizan como clase base:

|||
|-|-|
|[CMemoryException (clase)](../../mfc/reference/cmemoryexception-class.md)|Excepción de memoria insuficiente|
|[Clase CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Solicitudes de una operación no admitida|
|[Clase CResourceException](../../mfc/reference/cresourceexception-class.md)|Recurso de Windows no encontrado o no creable|
|[CUserException (clase)](../../mfc/reference/cuserexception-class.md)|Excepción que indica que no se pudo encontrar un recurso|
|[Clase CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Excepción que indica un argumento no válido|

Dado `CSimpleException` que es una clase base `CSimpleException` abstracta, no se puede declarar un objeto directamente. En su lugar, debe declarar objetos derivados como los de la tabla anterior. Si va a declarar su propia clase derivada, utilice las clases anteriores como modelo.

Para obtener más información, vea el tema [Clase CException](../../mfc/reference/cexception-class.md) y Control de [excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>CSimpleException::CSimpleException

El constructor.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*bAutoDelete*<br/>
Especifique TRUE si la `CSimpleException` memoria del objeto se ha asignado en el montón. Esto hará `CSimpleException` que el objeto `Delete` se elimine cuando se llama a la función miembro para eliminar la excepción. Especifique FALSE `CSimpleException` si el objeto está en la pila o es un objeto global. En este caso, el `CSimpleException` objeto no `Delete` se eliminará cuando se llama a la función miembro.

### <a name="remarks"></a>Observaciones

Normalmente nunca tendría que llamar a este constructor directamente. Una función que produce una excepción `CException`debe crear una instancia de una clase derivada y llamar a su constructor, o debe usar una de las funciones de inicio de MFC, como [AfxThrowFileException](exception-processing.md#afxthrowfileexception), para producir un tipo predefinido.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>CSimpleException::GetErrorMessage

Llame a esta función miembro para proporcionar texto sobre un error que se ha producido.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszError*<br/>
Puntero a un búfer que recibirá un mensaje de error.

*nMaxError*<br/>
El número máximo de caracteres que puede contener el búfer, incluido el terminador NULL.

*pnHelpContext*<br/>
La dirección de un UINT que recibirá el identificador de contexto de ayuda. Si NULL, no se devolverá ningún identificador.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0 si no hay texto de mensaje de error disponible.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Control de excepciones](../../mfc/exception-handling-in-mfc.md)
