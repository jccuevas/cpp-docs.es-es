---
title: CAsyncMonikerFile (clase)
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
ms.openlocfilehash: b86cba0c2e8f7991902a552d404355d6c1474138
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237867"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile (clase)

Proporciona funcionalidad para el uso de monikers asincrónicos en los controles ActiveX (antes controles OLE).

## <a name="syntax"></a>Sintaxis

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Construye un objeto `CAsyncMonikerFile`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|Cierra y libera todos los recursos.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Recupera un puntero a la transferencia asincrónica de enlace.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Recupera el formato de los datos de la secuencia.|
|[CAsyncMonikerFile::Open](#open)|Abre un archivo de forma asincrónica.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Crea un objeto COM que implementa `IBindStatusCallback`.|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Llama a la biblioteca del sistema OLE para solicitar información sobre el tipo de enlace que se va a crear.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Llama a la biblioteca del sistema OLE para obtener la prioridad del enlace.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a medida que estén disponible para el cliente durante las operaciones de enlace asincrónica.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Se llama cuando hay pocos recursos.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Se llama para indicar el progreso en el proceso de descarga de datos.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Se llama cuando el enlace se está iniciando.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia asincrónica.|

## <a name="remarks"></a>Comentarios

Deriva [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), que a su vez se deriva [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` usa el [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) interfaz para tener acceso a cualquier flujo de datos de forma asincrónica, como cargar archivos de forma asincrónica desde una dirección URL. Los archivos pueden ser propiedades de ruta de datos de los controles ActiveX.

Monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y los controles ActiveX para proporcionar una interfaz de usuario con capacidad de respuesta durante las transferencias de archivos. Un buen ejemplo de esto es el uso de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas para controles ActiveX. La `CDataPathProperty` objeto repetidamente obtendrá una devolución de llamada para indicar la disponibilidad de nuevos datos durante el proceso de exchange propiedad largas.

Para obtener más información sobre cómo usar controles ActiveX y monikers asincrónicos en aplicaciones de Internet, consulte los artículos siguientes:

- [Primeros pasos de Internet: Monikers asincrónicos](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Primeros pasos de Internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile

Construye un objeto `CAsyncMonikerFile`.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Comentarios

No se crea el `IBindHost` interfaz. `IBindHost` se usa solo si se proporciona en el `Open` función miembro.

Para obtener una descripción de la `IBindHost` interfaz, consulte el SDK de Windows.

##  <a name="close"></a>  CAsyncMonikerFile::Close

Llame a esta función para cerrar y liberar todos los recursos.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Se puede llamar en los archivos no abiertos o cerrados ya.

##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback

Crea un objeto COM que implementa `IBindStatusCallback`.

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parámetros

*pUnkControlling*<br/>
Un puntero a la desconocido de control (el exterior `IUnknown`) o NULL si no se utiliza la agregación.

### <a name="return-value"></a>Valor devuelto

Si *pUnkControlling* no es NULL, la función devuelve un puntero a la excepción interna `IUnknown` en un nuevo objeto COM admitidos `IBindStatusCallback`. Si `pUnkControlling` es NULL, la función devuelve un puntero a un `IUnknown` en un nuevo objeto COM admitidos `IBindStatusCallback`.

### <a name="remarks"></a>Comentarios

`CAsyncMonikerFile` requiere un objeto COM que implementa `IBindStatusCallback`. MFC implementa este tipo de objeto y es agregable. Se puede reemplazar `CreateBindStatusCallback` para devolver su propio objeto COM. El objeto COM puede agregar la implementación de MFC mediante una llamada a `CreateBindStatusCallback` con desconocido de control del objeto COM. Objetos COM que implementa mediante el `CCmdTarget` compatibilidad con COM puede recuperar el control desconocido usando `CCmdTarget::GetControllingUnknown`.

Como alternativa, puede delegar el objeto COM para la implementación de MFC mediante una llamada a `CreateBindStatusCallback( NULL )`.

[CAsyncMonikerFile::Open](#open) llamadas `CreateBindStatusCallback`.

Para obtener más información acerca de los monikers asincrónicos y enlace asincrónica, vea el [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) interfaz y [cómo enlace asincrónica y el trabajo de almacenamiento](/windows/desktop/Stg/how-asynchronous-binding-and-storage-work). Para obtener una explicación de agregación, vea [agregación](/windows/desktop/com/aggregation). Todos los tres temas están en el SDK de Windows.

##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo

Se llama desde el cliente de un moniker asincrónico para indicar que el moniker asincrónico cómo quiere enlazar.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Valor devuelto

Recupera los valores para `IBindStatusCallBack`. Para obtener una descripción de la `IBindStatusCallback` interfaz, consulte el SDK de Windows.

### <a name="remarks"></a>Comentarios

La implementación predeterminada establece el enlace sea asincrónico, para usar un medio de almacenamiento (transmisión) y utilizar el modelo de inserción de datos. Reemplace esta función si desea cambiar el comportamiento del enlace.

Un motivo para hacerlo sería para enlazar con el modelo de extracción de datos en lugar del modelo de inserción de datos. En un modelo de extracción de datos, el cliente controla la operación de enlace y el moniker solo proporciona datos al cliente cuando se lee. En un modelo de inserción de datos, el moniker controla la operación de enlace asincrónica y continuamente notifica al cliente cada vez que hay nuevos datos disponibles.

##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding

Llame a esta función para recuperar un puntero a la transferencia asincrónica de enlace.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la `IBinding` interfaz proporcionada cuando comienza la transferencia asincrónica. Devuelve NULL si por algún motivo la transferencia no se pueden realizar de forma asincrónica.

### <a name="remarks"></a>Comentarios

Esto le permite controlar la transferencia de datos proceso a través de la `IBinding` interfaz, por ejemplo, con `IBinding::Abort`, `IBinding::Pause`, y `IBinding::Resume`.

Para obtener una descripción de la `IBinding` interfaz, consulte el SDK de Windows.

##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc

Llame a esta función para recuperar el formato de los datos de la secuencia.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la estructura de Windows [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) para el flujo abierto actualmente. Devuelve NULL si el moniker no se ha enlazado, si no es asincrónico, o si no ha comenzado la operación asincrónica.

##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority

Se le llama desde el cliente de un moniker asincrónico cuando se inicia el proceso de enlace recibir la prioridad asignada al subproceso de la operación de enlace.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Valor devuelto

La prioridad en el que llevará a cabo la transferencia asincrónica. Una de las marcas de prioridad de subprocesos estándar: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL y THREAD_PRIORITY_TIME_CRITICAL. Vea la función Windows [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) para obtener una descripción de estos valores.

### <a name="remarks"></a>Comentarios

`GetPriority` no debe llamarse directamente. La implementación predeterminada devuelve THREAD_PRIORITY_NORMAL.

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

Un moniker asincrónico llama a `OnDataAvailable` para proporcionar datos al cliente cuando se encuentre disponible, asincrónica durante el enlace de operaciones.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parámetros

*dwSize*<br/>
La cantidad acumulada (en bytes) de datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante para la operación o que ninguna cantidad específica, empezó a estar disponible.

*bscfFlag*<br/>
Un valor de enumeración BSCF. Puede ser uno o varios de los siguientes valores:

- BSCF_FIRSTDATANOTIFICATION identifica la primera llamada a `OnDataAvailable` para una operación de enlace especificado.

- BSCF_INTERMEDIATEDATANOTIFICATION identifica una llamada al intermediaria `OnDataAvailable` para una operación de enlace.

- BSCF_LASTDATANOTIFICATION identifica la última llamada a `OnDataAvailable` para una operación de enlace.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función no hace nada. Vea el ejemplo siguiente de una implementación de ejemplo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

Llamado por el moniker cuando hay pocos recursos.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama `GetBinding( )-> Abort( )`.

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

Lo llama el moniker repetidamente para indicar el progreso actual de esta operación de enlace, normalmente a intervalos razonables durante una operación larga.

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
Indica el valor máximo esperado del *ulProgress* para la duración de las llamadas a `OnProgress` para esta operación.

*ulStatusCode*<br/>
Proporciona información adicional sobre el progreso de la operación de enlace. Los valores válidos se toman de la `BINDSTATUS` enumeración. Vea la sección Comentarios para los valores posibles.

*szStatusText*<br/>
Información sobre el progreso actual, dependiendo del valor de *ulStatusCode*. Vea la sección Comentarios para los valores posibles.

### <a name="remarks"></a>Comentarios

Los valores posibles de *ulStatusCode* (y el *szStatusText* para cada valor) son:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |La operación de enlace está buscando el recurso que contiene el objeto o el almacenamiento que se enlaza. El *szStatusText* proporciona el nombre para mostrar del recurso que se está buscando para (por ejemplo, "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |La operación de enlace se conecta al recurso que contiene el objeto o el almacenamiento que se enlaza. El *szStatusText* proporciona el nombre para mostrar del recurso que se está conectado a (por ejemplo, una dirección IP).  |
|BINDSTATUS_SENDINGREQUEST|La operación de enlace está solicitando el objeto o el almacenamiento que se enlaza. El *szStatusText* proporciona el nombre para mostrar del objeto (por ejemplo, un nombre de archivo).|
|BINDSTATUS_REDIRECTING  |La operación de enlace se ha redirigido a una ubicación de datos diferente. El *szStatusText* proporciona el nombre para mostrar de la nueva ubicación de datos.  |
|BINDSTATUS_USINGCACHEDCOPY  |La operación de enlace está recuperando el objeto solicitado o el almacenamiento desde una copia en caché. El *szStatusText* es NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |La operación de enlace ha comenzado a recibir el objeto o el almacenamiento que se enlaza. El *szStatusText* proporciona el nombre para mostrar de la ubicación de datos.|
|BINDSTATUS_DOWNLOADINGDATA  |La operación de enlace continúa recibiendo el objeto o el almacenamiento que se enlaza. El *szStatusText* proporciona el nombre para mostrar de la ubicación de datos.  |
|BINDSTATUS_ENDDOWNLOADDATA  |La operación de enlace ha terminado de recibir el objeto o el almacenamiento que se enlaza. El *szStatusText* proporciona el nombre para mostrar de la ubicación de datos.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Una instancia del objeto que se enlaza a está a punto de crearse. El *szStatusText* proporciona el CLSID del nuevo objeto en formato de cadena, que permite al cliente una oportunidad de cancelar la operación de enlace, si lo desea.  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

Reemplace esta función en sus clases derivadas para realizar acciones cuando el enlace se está iniciando.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Comentarios

Esta función se invoca de nuevo por el moniker. La implementación predeterminada no hace nada.

##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding

Lo llama el moniker al final de la operación de enlace.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parámetros

*hresult*<br/>
Un HRESULT de error o el valor de advertencia.

*szErrort*<br/>
Una cadena de caracteres que describe el error.

### <a name="remarks"></a>Comentarios

Reemplace esta función para realizar acciones cuando se detiene la transferencia. De forma predeterminada, la función libera `IBinding`.

Para obtener una descripción de la `IBinding` interfaz, consulte el SDK de Windows.

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
Un puntero al archivo que se va a abrirse de forma asincrónica. El archivo puede ser cualquier dirección URL o nombre de archivo válido.

*pError*<br/>
Un puntero a las excepciones del archivo. Si se produce un error, se establecerá la causa.

*pMoniker*<br/>
Un puntero a la interfaz de moniker asincrónico `IMoniker`, un moniker preciso que es la combinación del moniker del documento, que puede recuperar con `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`y un moniker creado a partir del nombre de ruta de acceso. El control puede usar este moniker para enlazar, pero esto no es el moniker que debe guardar el control.

*pBindHost*<br/>
Un puntero a la `IBindHost` interfaz que se usará para crear el moniker de una ruta de acceso potencialmente relativa. Si el host de enlace no es válido o no proporciona un moniker, la llamada tiene como valor predeterminado `Open(lpszFileName,pError)`. Para obtener una descripción de la `IBindHost` interfaz, consulte el SDK de Windows.

*pServiceProvider*<br/>
Puntero a la interfaz `IServiceProvider`. Si el proveedor de servicios no es válido o no proporciona el servicio para `IBindHost`, el valor predeterminado es la llamada a `Open(lpszFileName,pError)`.

*pUnknown*<br/>
Puntero a la interfaz `IUnknown`. Si `IServiceProvider` se encuentra, la función de consulta para `IBindHost`. Si el proveedor de servicios no es válido o no proporciona el servicio para `IBindHost`, el valor predeterminado es la llamada a `Open(lpszFileName,pError)`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se abrió correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta llamada inicia el proceso de enlace.

Puede usar una dirección URL o un nombre de archivo para el *lpszURL* parámetro. Por ejemplo:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- o -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Vea también

[CMonikerFile (clase)](../../mfc/reference/cmonikerfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile (clase)](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty (clase)](../../mfc/reference/cdatapathproperty-class.md)
