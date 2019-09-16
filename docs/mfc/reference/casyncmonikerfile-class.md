---
title: Clase CAsyncMonikerFile
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: cd399368e46e4e9a86b4c6260e07aee07b80defb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507500"
---
# <a name="casyncmonikerfile-class"></a>Clase CAsyncMonikerFile

Proporciona funcionalidad para el uso de monikers asincrónicos en los controles ActiveX (antes controles OLE).

## <a name="syntax"></a>Sintaxis

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Construye un objeto `CAsyncMonikerFile`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|Cierra y libera todos los recursos.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Recupera un puntero al enlace de transferencia asincrónico.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Recupera el formato de los datos de la secuencia.|
|[CAsyncMonikerFile::Open](#open)|Abre un archivo de forma asincrónica.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Crea un objeto COM que implementa `IBindStatusCallback`.|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|La biblioteca del sistema OLE lo llama para solicitar información sobre el tipo de enlace que se va a crear.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|La biblioteca del sistema OLE llama a esta función para obtener la prioridad del enlace.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a medida que están disponibles para el cliente durante las operaciones de enlace asincrónicas.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Se llama cuando los recursos son bajos.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Se llama para indicar el progreso en el proceso de descarga de datos.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Se llama cuando se está iniciando el enlace.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia asincrónica.|

## <a name="remarks"></a>Comentarios

Derivado de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), que a su vez se deriva de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` usa la interfaz [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) para tener acceso a cualquier flujo de datos de forma asincrónica, incluida la carga de archivos de forma asincrónica desde una dirección URL. Los archivos pueden ser propiedades de ruta de acceso de los controles ActiveX.

Los monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario con capacidad de respuesta durante las transferencias de archivos. Un ejemplo primo es el uso de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas para los controles ActiveX. El `CDataPathProperty` objeto obtendrá repetidamente una devolución de llamada para indicar la disponibilidad de los nuevos datos durante un proceso de intercambio de propiedades prolongado.

Para obtener más información sobre cómo usar monikers asincrónicos y controles ActiveX en aplicaciones de Internet, vea los siguientes artículos:

- [Primeros pasos de Internet: Monikers asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Primeros pasos de Internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile

Construye un objeto `CAsyncMonikerFile`.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Comentarios

No crea la `IBindHost` interfaz. `IBindHost`solo se usa si se proporciona en la `Open` función miembro.

Para obtener una descripción de `IBindHost` la interfaz, vea el Windows SDK.

##  <a name="close"></a>  CAsyncMonikerFile::Close

Llame a esta función para cerrar y liberar todos los recursos.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Se puede llamar a en archivos no abiertos o ya cerrados.

##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback

Crea un objeto COM que implementa `IBindStatusCallback`.

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parámetros

*pUnkControlling*<br/>
Puntero al control desconocido (externo `IUnknown`) o null si no se utiliza la agregación.

### <a name="return-value"></a>Valor devuelto

Si *pUnkControlling* no es null, la función devuelve un puntero al interior `IUnknown` en un nuevo objeto com que admite. `IBindStatusCallback` Si `pUnkControlling` es null, la función devuelve un puntero a una `IUnknown` en un nuevo objeto com que `IBindStatusCallback`admite.

### <a name="remarks"></a>Comentarios

`CAsyncMonikerFile`requiere un objeto COM que implementa `IBindStatusCallback`. MFC implementa este tipo de objeto y es agregable. Puede invalidar `CreateBindStatusCallback` para devolver su propio objeto com. El objeto com puede Agregar la implementación `CreateBindStatusCallback` de MFC llamando a con el control desconocido del objeto com. Los objetos com implementados `CCmdTarget` mediante la compatibilidad con com pueden recuperar el `CCmdTarget::GetControllingUnknown`control desconocido mediante.

Como alternativa, el objeto COM puede delegar a la implementación de MFC `CreateBindStatusCallback( NULL )`mediante una llamada a.

Llamadas a `CreateBindStatusCallback` [CAsyncMonikerFile:: Open](#open) .

Para obtener más información acerca de los monikers asincrónicos y el enlace asincrónico, vea la interfaz [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) y [Cómo funcionan el enlace asincrónico y el almacenamiento](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Para obtener una explicación de la agregación, vea [agregación](/windows/win32/com/aggregation). Los tres temas se encuentran en el Windows SDK.

##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo

Se llama desde el cliente de un moniker asincrónico para indicar al moniker asincrónico cómo desea enlazar.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Valor devuelto

Recupera la configuración para `IBindStatusCallBack`. Para obtener una descripción de `IBindStatusCallback` la interfaz, vea el Windows SDK.

### <a name="remarks"></a>Comentarios

La implementación predeterminada establece que el enlace sea asincrónico, para usar un medio de almacenamiento (un flujo) y para usar el modelo de entrada de datos. Reemplace esta función si desea cambiar el comportamiento del enlace.

Una razón para hacerlo sería enlazar con el modelo de extracción de datos en lugar del modelo de inserción de datos. En un modelo de extracción de datos, el cliente controla la operación de enlace y el moniker solo proporciona datos al cliente cuando se lee. En un modelo de extracción de datos, el moniker controla la operación de enlace asincrónica y notifica continuamente al cliente cada vez que haya nuevos datos disponibles.

##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding

Llame a esta función para recuperar un puntero al enlace de transferencia asincrónico.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la `IBinding` interfaz proporcionada cuando comienza la transferencia asincrónica. Devuelve NULL si por alguna razón no se puede realizar la transferencia de forma asincrónica.

### <a name="remarks"></a>Comentarios

Esto le permite controlar el proceso de transferencia de datos a `IBinding` través de la interfaz, por `IBinding::Abort`ejemplo `IBinding::Pause`, con `IBinding::Resume`, y.

Para obtener una descripción de `IBinding` la interfaz, vea el Windows SDK.

##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc

Llame a esta función para recuperar el formato de los datos de la secuencia.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la estructura de Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) para la secuencia abierta actualmente. Devuelve NULL si no se ha enlazado el moniker, si no es asincrónico, o si la operación asincrónica no ha empezado.

##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority

Se llama desde el cliente de un moniker asincrónico a medida que el proceso de enlace comienza a recibir la prioridad dada al subproceso de la operación de enlace.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Valor devuelto

La prioridad con la que se llevará a cabo la transferencia asincrónica. Una de las marcas de prioridad de subproceso estándar: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL y THREAD_PRIORITY_TIME_CRITICAL. Vea la función [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) de Windows para obtener una descripción de estos valores.

### <a name="remarks"></a>Comentarios

`GetPriority`no se debe llamar directamente a. La implementación predeterminada devuelve THREAD_PRIORITY_NORMAL.

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

Un moniker asincrónico `OnDataAvailable` llama a para proporcionar datos al cliente cuando está disponible, durante las operaciones de enlace asincrónicas.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parámetros

*dwSize*<br/>
Cantidad acumulativa (en bytes) de los datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante para la operación o que no hay ningún importe específico disponible.

*bscfFlag*<br/>
Valor de enumeración BSCF. Puede ser uno o varios de los valores siguientes:

- BSCF_FIRSTDATANOTIFICATION identifica la primera llamada a `OnDataAvailable` para una operación de enlace determinada.

- BSCF_INTERMEDIATEDATANOTIFICATION identifica una llamada intermediaria a `OnDataAvailable` para una operación de enlace.

- BSCF_LASTDATANOTIFICATION identifica la última llamada a `OnDataAvailable` para una operación de enlace.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función no hace nada. Vea el ejemplo siguiente para obtener una implementación de ejemplo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

Llamado por el moniker cuando los recursos son bajos.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama `GetBinding( )-> Abort( )`a.

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

El moniker lo llama repetidamente para indicar el progreso actual de esta operación de enlace, normalmente a intervalos razonables durante una operación larga.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parámetros

*ulProgress*<br/>
Indica el progreso actual de la operación de enlace con respecto al máximo esperado indicado en *ulProgressMax*.

*ulProgressMax*<br/>
Indica el valor máximo esperado de *ulProgress* para la duración de las llamadas `OnProgress` a para esta operación.

*ulStatusCode*<br/>
Proporciona información adicional sobre el progreso de la operación de enlace. Los valores válidos se toman `BINDSTATUS` de la enumeración. Vea la sección Comentarios para ver los posibles valores.

*szStatusText*<br/>
Información sobre el progreso actual, dependiendo del valor de *ulStatusCode*. Vea la sección Comentarios para ver los posibles valores.

### <a name="remarks"></a>Comentarios

Los valores posibles para *ulStatusCode* (y *szstatustext del* para cada valor) son:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |La operación de enlace está buscando el recurso que contiene el objeto o el almacenamiento al que se está enlazando. *Szstatustext del* proporciona el nombre para mostrar del recurso que se va a buscar (por ejemplo, "www.Microsoft.com").  |
|BINDSTATUS_CONNECTING  |La operación de enlace se está conectando al recurso que contiene el objeto o el almacenamiento al que se está enlazando. *Szstatustext del* proporciona el nombre para mostrar del recurso al que se está conectando (por ejemplo, una dirección IP).  |
|BINDSTATUS_SENDINGREQUEST|La operación de enlace solicita el objeto o el almacenamiento al que se está enlazando. *Szstatustext del* proporciona el nombre para mostrar del objeto (por ejemplo, un nombre de archivo).|
|BINDSTATUS_REDIRECTING  |La operación de enlace se ha redirigido a una ubicación de datos diferente. *Szstatustext del* proporciona el nombre para mostrar de la nueva ubicación de datos.  |
|BINDSTATUS_USINGCACHEDCOPY  |La operación de enlace está recuperando el objeto solicitado o el almacenamiento de una copia almacenada en caché. El valor de *szstatustext del* es NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |La operación de enlace comenzó a recibir el objeto o el almacenamiento al que se está enlazando. *Szstatustext del* proporciona el nombre para mostrar de la ubicación de los datos.|
|BINDSTATUS_DOWNLOADINGDATA  |La operación de enlace continúa recibiendo el objeto o el almacenamiento al que se está enlazando. *Szstatustext del* proporciona el nombre para mostrar de la ubicación de los datos.  |
|BINDSTATUS_ENDDOWNLOADDATA  |La operación de enlace ha terminado de recibir el objeto o el almacenamiento al que se está enlazando. *Szstatustext del* proporciona el nombre para mostrar de la ubicación de los datos.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Una instancia del objeto que se está enlazando está a punto de crearse. *Szstatustext del* proporciona el CLSID del nuevo objeto en formato de cadena, lo que permite al cliente cancelar la operación de enlace, si se desea.  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

Invalide esta función en las clases derivadas para realizar acciones cuando se inicia el enlace.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Comentarios

El moniker llama a esta función. La implementación predeterminada no hace nada.

##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding

Llamado por el moniker al final de la operación de enlace.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parámetros

*hresult*<br/>
HRESULT que es el valor de error o de advertencia.

*szErrort*<br/>
Cadena de caracteres que describe el error.

### <a name="remarks"></a>Comentarios

Invalide esta función para realizar acciones cuando se detenga la transferencia. De forma predeterminada, la función `IBinding`libera.

Para obtener una descripción de `IBinding` la interfaz, vea el Windows SDK.

##  <a name="open"></a>  CAsyncMonikerFile::Open

Llame a esta función miembro para abrir un archivo de forma asincrónica.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
Puntero al archivo que se va a abrir de forma asincrónica. El archivo puede ser cualquier dirección URL o nombre de archivo válido.

*pError*<br/>
Un puntero a las excepciones de archivo. En caso de que se produzca un error, se establecerá en la causa.

*pMoniker*<br/>
Puntero a la interfaz `IMoniker`de moniker asincrónica, un moniker preciso que es la combinación del propio moniker del documento, que se puede recuperar con `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`y un moniker creado a partir del nombre de ruta de acceso. El control puede utilizar este moniker para enlazar, pero éste no es el moniker que debe guardar el control.

*pBindHost*<br/>
Un puntero a la `IBindHost` interfaz que se usará para crear el moniker a partir de un nombreruta potencialmente relativo. Si el host de enlace no es válido o no proporciona un moniker, la llamada `Open(lpszFileName,pError)`tiene como valor predeterminado. Para obtener una descripción de `IBindHost` la interfaz, vea el Windows SDK.

*pServiceProvider*<br/>
Puntero a la interfaz `IServiceProvider`. Si el proveedor de servicios no es válido o no proporciona el servicio `IBindHost`para, la llamada tiene como `Open(lpszFileName,pError)`valor predeterminado.

*pUnknown*<br/>
Puntero a la interfaz `IUnknown`. Si `IServiceProvider` se encuentra, la función `IBindHost`consulta. Si el proveedor de servicios no es válido o no proporciona el servicio `IBindHost`para, la llamada tiene como `Open(lpszFileName,pError)`valor predeterminado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se abre correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta llamada inicia el proceso de enlace.

Puede usar una dirección URL o un nombre de archivo para el parámetro *lpszURL* . Por ejemplo:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- o -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Vea también

[CMonikerFile (clase)](../../mfc/reference/cmonikerfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile (clase)](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty (clase)](../../mfc/reference/cdatapathproperty-class.md)
