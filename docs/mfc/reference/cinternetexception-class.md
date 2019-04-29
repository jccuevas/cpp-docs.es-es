---
title: CInternetException (clase)
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: dedf8926f02dd36dc8d6ac8ab5ff4056b60dfc91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345713"
---
# <a name="cinternetexception-class"></a>CInternetException (clase)

Representa una condición de excepción relacionada con una operación de Internet.

## <a name="syntax"></a>Sintaxis

```
class CInternetException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Construye un objeto `CInternetException`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|El valor de contexto asociado con la operación que produjo la excepción.|
|[CInternetException::m_dwError](#m_dwerror)|El error que provocó la excepción.|

## <a name="remarks"></a>Comentarios

La `CInternetException` clase incluye dos miembros de datos públicos: uno contiene el código de error asociado con la excepción y la otra contiene el identificador de contexto de la aplicación de Internet asociado con el error.

Para obtener más información acerca de los identificadores de contexto para las aplicaciones de Internet, consulte el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="cinternetexception"></a>  CInternetException::CInternetException

Esta función miembro se llama cuando un `CInternetException` se crea el objeto.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parámetros

*dwError*<br/>
El error que provocó la excepción.

### <a name="remarks"></a>Comentarios

Para producir un CInternetException, llame a la función global de MFC [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

El valor de contexto asociado con la operación de Internet relacionada.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Comentarios

El identificador de contexto se especificó originalmente en [CInternetSession](../../mfc/reference/cinternetsession-class.md) y pasa por MFC a [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- y [CInternetFile](../../mfc/reference/cinternetfile-class.md)-las clases derivadas. Puede invalidar este comportamiento predeterminado y asignar cualquiera *dwContext* parámetro un valor de su elección. *dwContext* está asociado a cualquier operación del objeto especificado. *dwContext* identifica información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

El error que provocó la excepción.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Comentarios

Este valor de error puede ser un sistema de código de error, se encuentra en el archivo WINERROR. H o un valor de error de WININET. H.

Para obtener una lista de códigos de error de Win32, vea [códigos de Error](/windows/desktop/Debug/system-error-codes). Para obtener una lista de mensajes de error específicos de Internet, consulte. Ambos temas se encuentran en el SDK de Windows.

## <a name="see-also"></a>Vea también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)
