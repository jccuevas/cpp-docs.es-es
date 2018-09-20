---
title: CSimpleException (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f25928243c8086462f4f35b47dee5239a3a240bf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447003"
---
# <a name="csimpleexception-class"></a>CSimpleException (clase)

Esta clase es una clase base para excepciones MFC de recursos críticos.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|Proporciona texto sobre un error que se ha producido.|

## <a name="remarks"></a>Comentarios

`CSimpleException` es la clase base para las excepciones de MFC recursos críticos y controla la propiedad e inicialización de un mensaje de error. Las siguientes clases utilizan `CSimpleException` como su clase base:

|||
|-|-|
|[CMemoryException (clase)](../../mfc/reference/cmemoryexception-class.md)|Excepción de memoria insuficiente|
|[CNotSupportedException (clase)](../../mfc/reference/cnotsupportedexception-class.md)|Solicitudes de una operación no admitida|
|[CResourceException (clase)](../../mfc/reference/cresourceexception-class.md)|Recursos de Windows no se encuentra o no se pueden crear|
|[CUserException (clase)](../../mfc/reference/cuserexception-class.md)|No se encontró la excepción que indica un recurso|
|[CInvalidArgException (clase)](../../mfc/reference/cinvalidargexception-class.md)|Excepción que indica un argumento no válido|

Dado que `CSimpleException` es una clase base abstracta, no puede declarar un `CSimpleException` objeto directamente. En su lugar, debe declarar objetos derivados, como los de la tabla anterior. Si va a declarar su propia clase derivada, utilice las clases anteriores como un modelo.

Para obtener más información, consulte el [clase CException](../../mfc/reference/cexception-class.md) tema y [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="csimpleexception"></a>  CSimpleException::CSimpleException

El constructor.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*bAutoDelete*<br/>
Especifique "true" si la memoria para el `CSimpleException` se asignó el objeto en el montón. Esto hará que el `CSimpleException` objeto que se eliminará cuando el `Delete` función miembro se llama para eliminar la excepción. Especifique FALSE si el `CSimpleException` objeto está en la pila o es un objeto global. En este caso, el `CSimpleException` objeto no se podrá eliminar cuando el `Delete` se llama a la función miembro.

### <a name="remarks"></a>Comentarios

General, nunca necesitará llamar directamente a este constructor. Una función que produce una excepción debe crear una instancia de un `CException`-clase derivada y llamar a su constructor, o bien debe usar uno de MFC throw funciones, como [AfxThrowFileException](exception-processing.md#afxthrowfileexception), inicien un tipo predefinido.

##  <a name="geterrormessage"></a>  CSimpleException::GetErrorMessage

Llame a esta función miembro para proporcionar el texto sobre un error que se ha producido.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszError*<br/>
Un puntero a un búfer que recibirá un mensaje de error.

*nMaxError*<br/>
El número máximo de caracteres que puede contener el búfer, incluido el terminador NULL.

*pnHelpContext*<br/>
La dirección de un tipo UINT que recibirá el identificador de contexto de ayuda. Si es NULL, no se devolverá ningún identificador.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, devuelve 0 si ningún error de texto del mensaje está disponible.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Control de excepciones](../../mfc/exception-handling-in-mfc.md)



