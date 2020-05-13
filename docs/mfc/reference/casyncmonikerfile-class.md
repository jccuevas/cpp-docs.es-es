---
title: CAsyncMonikerFile (Clase)
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
ms.openlocfilehash: 57ab463445f249b4e9393f19af103b7588962d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376993"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile (Clase)

Proporciona funcionalidad para el uso de monikers asincrónicos en los controles ActiveX (antes controles OLE).

## <a name="syntax"></a>Sintaxis

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Construye un objeto `CAsyncMonikerFile`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncMonikerFile::Cerrar](#close)|Cierra y libera todos los recursos.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Recupera un puntero al enlace de transferencia asincrónica.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Recupera el formato de los datos de la secuencia.|
|[CAsyncMonikerFile::Abrir](#open)|Abre un archivo de forma asincrónica.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Crea un objeto COM `IBindStatusCallback`que implementa .|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Llamado por la biblioteca del sistema OLE para solicitar información sobre el tipo de enlace que se va a crear.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Llamado por la biblioteca del sistema OLE para obtener la prioridad del enlace.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a medida que estén disponibles para el cliente durante las operaciones de enlace asincrónicas.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Se llama cuando los recursos son bajos.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Se llama para indicar el progreso en el proceso de descarga de datos.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Se llama cuando se inicia el enlace.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia asincrónica.|

## <a name="remarks"></a>Observaciones

Derivado de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), que a su vez se `CAsyncMonikerFile` deriva de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), utiliza la interfaz [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) para tener acceso a cualquier secuencia de datos de forma asincrónica, incluida la carga asincrónica de archivos desde una dirección URL. Los archivos pueden ser propiedades de ruta de datos de controles ActiveX.

Los monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario adaptable durante las transferencias de archivos. Un ejemplo principal de esto es el uso de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas para controles ActiveX. El `CDataPathProperty` objeto obtendrá repetidamente una devolución de llamada para indicar la disponibilidad de nuevos datos durante un largo proceso de intercambio de propiedades.

Para obtener más información acerca de cómo utilizar monikers asincrónicos y controles ActiveX en aplicaciones de Internet, consulte los siguientes artículos:

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

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile

Construye un objeto `CAsyncMonikerFile`.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Observaciones

No crea la `IBindHost` interfaz. `IBindHost`se utiliza solo si se `Open` proporciona en la función miembro.

Para obtener una `IBindHost` descripción de la interfaz, consulte el Windows SDK.

## <a name="casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Cerrar

Llame a esta función para cerrar y liberar todos los recursos.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Se puede llamar en archivos sin abrir o ya cerrados.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback

Crea un objeto COM `IBindStatusCallback`que implementa .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parámetros

*pUnkControlling*<br/>
Un puntero a la desconocida `IUnknown`de control (el externo ) o NULL si no se utiliza la agregación.

### <a name="return-value"></a>Valor devuelto

Si *pUnkControlling* no es NULL, la función devuelve un puntero al interior `IUnknown` de un nuevo objeto COM que admite `IBindStatusCallback`. Si `pUnkControlling` es NULL, la función `IUnknown` devuelve un puntero `IBindStatusCallback`a un objeto COM nuevo que admite .

### <a name="remarks"></a>Observaciones

`CAsyncMonikerFile`requiere un objeto COM `IBindStatusCallback`que implemente . MFC implementa un objeto de este tipo y es agregable. Puede invalidar `CreateBindStatusCallback` para devolver su propio objeto COM. El objeto COM puede agregar la `CreateBindStatusCallback` implementación de MFC llamando a la desconocida de control del objeto COM. Los objetos COM `CCmdTarget` implementados mediante la compatibilidad `CCmdTarget::GetControllingUnknown`con COM pueden recuperar el control desconocido mediante .

Como alternativa, el objeto COM puede delegar `CreateBindStatusCallback( NULL )`en la implementación de MFC llamando a .

[CAsyncMonikerFile::Open](#open) `CreateBindStatusCallback`llama .

Para obtener más información acerca de los monikers asincrónicos y el enlace asincrónico, vea la interfaz [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) y Cómo funcionan el enlace y almacenamiento [asincrónicos](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Para obtener una explicación de la agregación, vea [Agregación](/windows/win32/com/aggregation). Los tres temas se encuentran en el Windows SDK.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo

Se llama desde el cliente de un moniker asincrónico para indicar al moniker asincrónico cómo desea enlazar.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Valor devuelto

Recupera la configuración `IBindStatusCallBack`de . Para obtener una `IBindStatusCallback` descripción de la interfaz, consulte el Windows SDK.

### <a name="remarks"></a>Observaciones

La implementación predeterminada establece el enlace para que sea asincrónico, para usar un medio de almacenamiento (una secuencia) y para usar el modelo de inserción de datos. Invalide esta función si desea cambiar el comportamiento del enlace.

Una razón para hacer esto sería enlazar usando el modelo de extracción de datos en lugar del modelo de inserción de datos. En un modelo de extracción de datos, el cliente controla la operación de enlace y el moniker solo proporciona datos al cliente cuando se lee. En un modelo de inserción de datos, el moniker controla la operación de enlace asincrónica y notifica continuamente al cliente cada vez que hay nuevos datos disponibles.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMonikerFile::GetBinding

Llame a esta función para recuperar un puntero al enlace de transferencia asincrónica.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero `IBinding` a la interfaz proporcionada cuando comienza la transferencia asincrónica. Devuelve NULL si por cualquier motivo la transferencia no se puede realizar de forma asincrónica.

### <a name="remarks"></a>Observaciones

Esto le permite controlar el proceso `IBinding` de transferencia de `IBinding::Abort` `IBinding::Pause`datos `IBinding::Resume`a través de la interfaz, por ejemplo, con , , y .

Para obtener una `IBinding` descripción de la interfaz, consulte el Windows SDK.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc

Llame a esta función para recuperar el formato de los datos de la secuencia.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la estructura de Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) para la secuencia abierta actualmente. Devuelve NULL si el moniker no se ha enlazado, si no es asincrónico o si la operación asincrónica no ha comenzado.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority

Se llama desde el cliente de un moniker asincrónico como el proceso de enlace comienza a recibir la prioridad dada al subproceso para la operación de enlace.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Valor devuelto

La prioridad con la que tendrá lugar la transferencia asincrónica. Uno de los indicadores de prioridad de subproceso estándar: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL y THREAD_PRIORITY_TIME_CRITICAL. Consulte la función de Windows [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) para obtener una descripción de estos valores.

### <a name="remarks"></a>Observaciones

`GetPriority`no debe llamarse directamente. THREAD_PRIORITY_NORMAL devuelve la implementación predeterminada.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable

Un moniker `OnDataAvailable` asincrónico llama para proporcionar datos al cliente a medida que esté disponible, durante las operaciones de enlace asincrónicas.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parámetros

*dwSize*<br/>
La cantidad acumulada (en bytes) de datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante para la operación o que no se ha disponible ninguna cantidad específica.

*bscfFlag*<br/>
Un valor de enumeración BSCF. Puede ser uno o más de los siguientes valores:

- BSCF_FIRSTDATANOTIFICATION Identifica la primera `OnDataAvailable` llamada para una operación de enlace determinada.

- BSCF_INTERMEDIATEDATANOTIFICATION Identifica una llamada `OnDataAvailable` intermedia para una operación de enlace.

- BSCF_LASTDATANOTIFICATION Identifica la última `OnDataAvailable` llamada para una operación de enlace.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada. Consulte el ejemplo siguiente para obtener una implementación de ejemplo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource

Llamado por el apodo cuando los recursos son bajos.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Observaciones

La implementación `GetBinding( )-> Abort( )`predeterminada llama a .

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress

Llamado por el moniker repetidamente para indicar el progreso actual de esta operación de enlace, normalmente a intervalos razonables durante una operación larga.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parámetros

*ulProgress*<br/>
Indica el progreso actual de la operación de enlace en relación con el máximo esperado indicado en *ulProgressMax*.

*ulProgressMax*<br/>
Indica el valor máximo esperado de *ulProgress* `OnProgress` para la duración de las llamadas a esta operación.

*ulStatusCode*<br/>
Proporciona información adicional sobre el progreso de la operación de enlace. Los valores válidos `BINDSTATUS` se toman de la enumeración. Para obtener los valores posibles, vea la sección Comentarios.

*szStatusText*<br/>
Información sobre el progreso actual, en función del valor de *ulStatusCode*. Para obtener los valores posibles, vea la sección Comentarios.

### <a name="remarks"></a>Observaciones

Los valores posibles para *ulStatusCode* (y *szStatusText* para cada valor) son:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |La operación de enlace está buscando el recurso que contiene el objeto o almacenamiento al que se enlaza. El *szStatusText* proporciona el nombre para mostrar del recurso que se busca (por ejemplo, "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |La operación de enlace se conecta al recurso que contiene el objeto o el almacenamiento al que se enlaza. El *szStatusText* proporciona el nombre para mostrar del recurso al que se está conectando (por ejemplo, una dirección IP).  |
|BINDSTATUS_SENDINGREQUEST|La operación de enlace solicita que el objeto o el almacenamiento se enlacen a. El *szStatusText* proporciona el nombre para mostrar del objeto (por ejemplo, un nombre de archivo).|
|BINDSTATUS_REDIRECTING  |La operación de enlace se ha redirigido a una ubicación de datos diferente. El *szStatusText* proporciona el nombre para mostrar de la nueva ubicación de datos.  |
|BINDSTATUS_USINGCACHEDCOPY  |La operación de enlace está recuperando el objeto o almacenamiento solicitado de una copia almacenada en caché. El *szStatusText* es NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |La operación de enlace ha comenzado a recibir el objeto o el almacenamiento al que se enlaza. El *szStatusText* proporciona el nombre para mostrar de la ubicación de datos.|
|BINDSTATUS_DOWNLOADINGDATA  |La operación de enlace sigue recibiendo el objeto o el almacenamiento al que se enlaza. El *szStatusText* proporciona el nombre para mostrar de la ubicación de datos.  |
|BINDSTATUS_ENDDOWNLOADDATA  |La operación de enlace ha terminado de recibir el objeto o el almacenamiento al que se enlaza. El *szStatusText* proporciona el nombre para mostrar de la ubicación de datos.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Una instancia del objeto al que se enlaza está a punto de crearse. El *szStatusText* proporciona el CLSID del nuevo objeto en formato de cadena, lo que permite al cliente la oportunidad de cancelar la operación de enlace, si lo desea.  |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding

Invalide esta función en las clases derivadas para realizar acciones al iniciar el enlace.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Observaciones

El moniker llama a esta función. La implementación predeterminada no hace nada.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding

Llamado por el apodo al final de la operación de enlace.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parámetros

*Hresult*<br/>
Un HRESULT que es el valor de error o advertencia.

*szErrort*<br/>
Cadena de caracteres que describe el error.

### <a name="remarks"></a>Observaciones

Reemplace esta función para realizar acciones cuando se detenga la transferencia. De forma predeterminada, `IBinding`la función libera .

Para obtener una `IBinding` descripción de la interfaz, consulte el Windows SDK.

## <a name="casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Abrir

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
Puntero a archivo que se abrirá de forma asincrónica. El archivo puede ser cualquier URL o nombre de archivo válido.

*pError*<br/>
Un puntero a las excepciones de archivo. En caso de error, se establecerá en la causa.

*pMoniker*<br/>
Un puntero a la `IMoniker`interfaz de moniker asincrónica , un moniker preciso que es `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`la combinación del propio moniker del documento, que se puede recuperar con , y un moniker creado a partir del nombre de la ruta de acceso. El control puede usar este moniker para enlazar, pero este no es el moniker que el control debe guardar.

*pBindHost*<br/>
Puntero a `IBindHost` la interfaz que se usará para crear el moniker a partir de un nombre de ruta de acceso potencialmente relativo. Si el host de enlace no es válido o no `Open(lpszFileName,pError)`proporciona un moniker, el valor predeterminado de la llamada es . Para obtener una `IBindHost` descripción de la interfaz, consulte el Windows SDK.

*pServiceProvider*<br/>
Puntero a la interfaz `IServiceProvider`. Si el proveedor de servicios no es `IBindHost`válido o no `Open(lpszFileName,pError)`puede proporcionar el servicio para , el valor predeterminado de la llamada es .

*pDesconocido*<br/>
Puntero a la interfaz `IUnknown`. Si `IServiceProvider` se encuentra, la `IBindHost`función consulta . Si el proveedor de servicios no es `IBindHost`válido o no `Open(lpszFileName,pError)`puede proporcionar el servicio para , el valor predeterminado de la llamada es .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se abre correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta llamada inicia el proceso de enlace.

Puede utilizar una dirección URL o un nombre de archivo para el parámetro *lpszURL.* Por ejemplo:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- o -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Consulte también

[CMonikerFile (Clase)](../../mfc/reference/cmonikerfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile (Clase)](../../mfc/reference/cmonikerfile-class.md)<br/>
[Clase CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
