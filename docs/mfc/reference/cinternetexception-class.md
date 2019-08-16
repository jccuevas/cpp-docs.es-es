---
title: Clase CInternetException
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
ms.openlocfilehash: c4f4c7a5b7594270aff9dfbc224e9a66ba09be3f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505906"
---
# <a name="cinternetexception-class"></a>Clase CInternetException

Representa una condición de excepción relacionada con una operación de Internet.

## <a name="syntax"></a>Sintaxis

```
class CInternetException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Construye un objeto `CInternetException`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Valor de contexto asociado a la operación que produjo la excepción.|
|[CInternetException::m_dwError](#m_dwerror)|Error que produjo la excepción.|

## <a name="remarks"></a>Comentarios

La `CInternetException` clase incluye dos miembros de datos públicos: uno contiene el código de error asociado a la excepción y el otro contiene el identificador de contexto de la aplicación de Internet asociada al error.

Para obtener más información sobre los identificadores de contexto de las aplicaciones de Internet, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException (](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="cinternetexception"></a>  CInternetException::CInternetException

Se llama a esta función miembro cuando `CInternetException` se crea un objeto.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parámetros

*dwError*<br/>
Error que produjo la excepción.

### <a name="remarks"></a>Comentarios

Para iniciar una CInternetException, llame a la función global [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)de MFC.

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

Valor de contexto asociado a la operación de Internet relacionada.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Comentarios

El identificador de contexto se especifica originalmente en [CInternetSession](../../mfc/reference/cinternetsession-class.md) y lo pasa MFC a las clases derivadas de [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)-y [CInternetFile](../../mfc/reference/cinternetfile-class.md). Puede invalidar este valor predeterminado y asignar a cualquier parámetro *dwContext* un valor de su elección. *dwContext* está asociado a cualquier operación del objeto especificado. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

Error que produjo la excepción.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Comentarios

Este valor de error puede ser un código de error del sistema, que se encuentra en WINERROR. H o un valor de error de WININET. C.

Para obtener una lista de códigos de error de Win32, vea [códigos de error](/windows/win32/Debug/system-error-codes). Para obtener una lista de mensajes de error específicos de Internet, vea. Ambos temas se encuentran en el Windows SDK.

## <a name="see-also"></a>Vea también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)
