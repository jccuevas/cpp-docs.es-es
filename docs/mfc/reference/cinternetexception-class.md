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
ms.openlocfilehash: b0239afa2b984ccf93d661ec11f11013c89fd912
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372404"
---
# <a name="cinternetexception-class"></a>CInternetException (clase)

Representa una condición de excepción relacionada con una operación de Internet.

## <a name="syntax"></a>Sintaxis

```
class CInternetException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Construye un objeto `CInternetException`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|El valor de contexto asociado a la operación que causó la excepción.|
|[CInternetException::m_dwError](#m_dwerror)|Error que causó la excepción.|

## <a name="remarks"></a>Observaciones

La `CInternetException` clase incluye dos miembros de datos públicos: uno contiene el código de error asociado a la excepción y el otro contiene el identificador de contexto de la aplicación de Internet asociada al error.

Para obtener más información acerca de los identificadores de contexto para aplicaciones de Internet, consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException

Se llama a esta `CInternetException` función miembro cuando se crea un objeto.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parámetros

*dwError*<br/>
Error que causó la excepción.

### <a name="remarks"></a>Observaciones

Para iniciar una CInternetException, llame a la función global MFC [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

## <a name="cinternetexceptionm_dwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext

El valor de contexto asociado a la operación de Internet relacionada.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Observaciones

El identificador de contexto se especifica originalmente en [CInternetSession](../../mfc/reference/cinternetsession-class.md) y se pasa por MFC a [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- y [CInternetFile](../../mfc/reference/cinternetfile-class.md)-clases derivadas. Puede invalidar este valor predeterminado y asignar a cualquier parámetro *dwContext* un valor de su elección. *dwContext* está asociado a cualquier operación del objeto especificado. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

## <a name="cinternetexceptionm_dwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError

Error que causó la excepción.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Observaciones

Este valor de error puede ser un código de error del sistema, que se encuentra en WINERROR. H, o un valor de error de WININET. H.

Para obtener una lista de códigos de error De32, consulte [Códigos](/windows/win32/Debug/system-error-codes)de error . Para obtener una lista de mensajes de error específicos de Internet, consulte . Ambos temas se encuentran en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CException](../../mfc/reference/cexception-class.md)
