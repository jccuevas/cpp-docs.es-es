---
title: Clase CAsyncMonikerFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 546e251f3387175812e6ba7f8cfed5d8a878d658
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="casyncmonikerfile-class"></a>Clase CAsyncMonikerFile
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
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a medida que estén disponible para el cliente durante las operaciones de enlace asincrónico.|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Se llama cuando se están quedando sin recursos.|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|Se llama para indicar el progreso en el proceso de transferencia de datos.|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Se llama cuando el enlace se está iniciando.|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia asincrónica.|  
  
## <a name="remarks"></a>Comentarios  
 Derivado de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), que a su vez se deriva de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` utiliza la [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) interfaz para tener acceso a cualquier flujo de datos de forma asincrónica, incluidos cargar archivos de forma asincrónica desde una dirección URL. Los archivos pueden ser propiedades de ruta de datos de los controles de ActiveX.  
  
 Monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario siga respondiendo durante las transferencias de archivos. Un buen ejemplo de esto es el uso de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas para controles ActiveX. La `CDataPathProperty` objeto repetidamente obtendrá una devolución de llamada para indicar la disponibilidad de nuevos datos durante un proceso de intercambio de propiedad largo.  
  
 Para obtener más información sobre cómo usar controles de ActiveX y monikers asincrónicos en las aplicaciones de Internet, consulte los artículos siguientes:  
  
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
  
##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile  
 Construye un objeto `CAsyncMonikerFile`.  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>Comentarios  
 No se crea el `IBindHost` interfaz. `IBindHost`se usa únicamente si se proporciona en el **abiertos** función miembro.  
  
 Para obtener una descripción de la `IBindHost` interfaz, vea el SDK de Windows.  
  
##  <a name="close"></a>CAsyncMonikerFile::Close  
 Llame a esta función para cerrar y liberar todos los recursos.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede llamar en archivos abiertos o cerrados ya.  
  
##  <a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback  
 Crea un objeto COM que implementa `IBindStatusCallback`.  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkControlling`  
 Un puntero a la desconocido de control (el exterior **IUnknown**) o **NULL** si no se está utilizando agregaciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Si `pUnkControlling` no **NULL**, la función devuelve un puntero a interna **IUnknown** en un nuevo objeto COM admitidos `IBindStatusCallback`. Si `pUnkControlling` es **NULL**, la función devuelve un puntero a un **IUnknown** en un nuevo objeto COM admitidos `IBindStatusCallback`.  
  
### <a name="remarks"></a>Comentarios  
 `CAsyncMonikerFile`requiere un objeto COM que implementa `IBindStatusCallback`. MFC implementa este tipo de objeto y es agregable. Se puede reemplazar `CreateBindStatusCallback` para devolver su propio objeto COM. El objeto COM puede agregar la implementación de MFC mediante una llamada a `CreateBindStatusCallback` con desconocido de control del objeto COM. Objetos COM implementados mediante el `CCmdTarget` compatibilidad con COM puede recuperar el control con desconocido **CCmdTarget::GetControllingUnknown**.  
  
 Como alternativa, puede delegar el objeto COM para la implementación de MFC mediante una llamada a **CreateBindStatusCallback (NULL)**.  
  
 [CAsyncMonikerFile::Open](#open) llamadas `CreateBindStatusCallback`.  
  
 Para obtener más información sobre los monikers asincrónicos y el enlace asincrónica, vea el [IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060) interfaz y [cómo enlace asíncrono y trabajo de almacenamiento](http://msdn.microsoft.com/library/windows/desktop/aa379152). Para obtener una explicación de agregación, vea [agregaciones](http://msdn.microsoft.com/library/windows/desktop/ms686558). Todos los tres temas se encuentran en el SDK de Windows.  
  
##  <a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo  
 Se llama desde el cliente de un moniker asincrónico para indicar que el moniker asincrónico cómo va a enlazar.  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera la configuración de **IBindStatusCallBack**. Para obtener una descripción de la `IBindStatusCallback` interfaz, vea el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada establece el enlace que se va a ser asincrónica para utilizar un medio de almacenamiento (un objeto stream) y debe usar el modelo de inserción de datos. Reemplace esta función si desea cambiar el comportamiento del enlace.  
  
 Una razón para hacerlo sería enlazar con el modelo de extracción de datos en lugar del modelo de inserción de datos. En un modelo de extracción de datos, el cliente de las unidades de la operación de enlace y el moniker sólo proporciona datos para el cliente cuando se leen. En un modelo de inserción de datos, el moniker impulsa la operación de enlace asincrónico y continuamente notifica al cliente cada vez que hay nuevos datos disponibles.  
  
##  <a name="getbinding"></a>CAsyncMonikerFile::GetBinding  
 Llame a esta función para recuperar un puntero a la transferencia asincrónica de enlace.  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `IBinding` interfaz proporcionada cuando comienza la transferencia asincrónica. Devuelve **NULL** si por alguna razón la transferencia no puede realizarse de manera asincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Esto le permite controlar la transferencia de datos proceso a través de la `IBinding` interfaz, por ejemplo, con **IBinding::Abort**, **IBinding::Pause**, y **IBinding::Resume**.  
  
 Para obtener una descripción de la `IBinding` interfaz, vea el SDK de Windows.  
  
##  <a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc  
 Llame a esta función para recuperar el formato de los datos de la secuencia.  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la estructura de Windows [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) para la secuencia abierta actualmente. Devuelve **NULL** si el moniker no se ha enlazado, si no es asincrónico, o si no ha comenzado la operación asincrónica.  
  
##  <a name="getpriority"></a>CAsyncMonikerFile::GetPriority  
 Llamado desde el cliente de un moniker asincrónico al iniciar el proceso de enlace recibir la prioridad que se asigna al subproceso para la operación de enlace.  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La prioridad en el que llevará a cabo la transferencia asincrónica. Uno de los indicadores de prioridad de subproceso estándar: **THREAD_PRIORITY_ABOVE_NORMAL**, **THREAD_PRIORITY_BELOW_NORMAL**, **THREAD_PRIORITY_HIGHEST**,  **THREAD_PRIORITY_IDLE**, **THREAD_PRIORITY_LOWEST**, **THREAD_PRIORITY_NORMAL**, y **THREAD_PRIORITY_TIME_CRITICAL**. Vea la función de Windows [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) para obtener una descripción de estos valores.  
  
### <a name="remarks"></a>Comentarios  
 `GetPriority`no debe llamarse directamente. **THREAD_PRIORITY_NORMAL** devuelto por la implementación predeterminada.  
  
##  <a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable  
 Un moniker asincrónico llama `OnDataAvailable` para proporcionar datos al cliente cuando se encuentre disponible, durante asincrónica enlazar las operaciones.  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwSize`  
 La cantidad acumulativa (en bytes) de los datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante para la operación, o que ninguna cantidad específica, empezó a estar disponible.  
  
 *bscfFlag*  
 A **BSCF** valor de enumeración. Puede ser uno o varios de los siguientes valores:  
  
- **BSCF_FIRSTDATANOTIFICATION** identifica la primera llamada a `OnDataAvailable` para una operación de enlace especificado.  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION** identifica una llamada al intermediaria `OnDataAvailable` para una operación de enlace.  
  
- **BSCF_LASTDATANOTIFICATION** identifica la última llamada a `OnDataAvailable` para una operación de enlace.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Vea el ejemplo siguiente para una implementación de ejemplo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource  
 Llamado por el moniker cuando hay pocos recursos.  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `GetBinding( )-> Abort( )`.  
  
##  <a name="onprogress"></a>CAsyncMonikerFile::OnProgress  
 Llamado por el moniker repetidamente para indicar el progreso actual de esta operación de enlace, por lo general a intervalos razonables durante una operación larga.  
  
```  
virtual void OnProgress(
    ULONG ulProgress,  
    ULONG ulProgressMax,  
    ULONG ulStatusCode,  
    LPCTSTR szStatusText);
```  
  
### <a name="parameters"></a>Parámetros  
 `ulProgress`  
 Indica el progreso actual de la operación de enlace en relación con el máximo esperado indicado en `ulProgressMax`.  
  
 `ulProgressMax`  
 Indica el valor máximo esperado de `ulProgress` para la duración de las llamadas a `OnProgress` para esta operación.  
  
 `ulStatusCode`  
 Proporciona información adicional sobre el progreso de la operación de enlace. Los valores válidos se toman de la `BINDSTATUS` enumeración. Vea la sección Comentarios para los valores posibles.  
  
 `szStatusText`  
 Información sobre el progreso actual, dependiendo del valor de `ulStatusCode`. Vea la sección Comentarios para los valores posibles.  
  
### <a name="remarks"></a>Comentarios  
 Valores posibles de `ulStatusCode` (y el `szStatusText` para cada valor) son:  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 Detecta el recurso que contiene el objeto o el almacenamiento que se enlaza a la operación de enlace. El `szStatusText` proporciona el nombre para mostrar del recurso que se va a buscar para (por ejemplo, "www.microsoft.com").  
  
 **BINDSTATUS_CONNECTING**  
 Se está conectando al recurso que contiene el objeto o el almacenamiento que se enlaza a la operación de enlace. El `szStatusText` proporciona el nombre para mostrar del recurso que se está conectado a (por ejemplo, una dirección IP).  
  
 **BINDSTATUS_SENDINGREQUEST**  
 La operación de enlace está solicitando el almacenamiento que se enlaza a o el objeto. El `szStatusText` proporciona el nombre para mostrar del objeto (por ejemplo, un nombre de archivo).  
  
 **BINDSTATUS_REDIRECTING**  
 La operación de enlace se ha redirigido a una ubicación de datos diferente. El `szStatusText` proporciona el nombre para mostrar de la nueva ubicación de datos.  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 La operación de enlace está recuperando el objeto solicitado o almacenamiento de una copia en caché. El `szStatusText` es **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 La operación de enlace ha comenzado a recibir el objeto o el almacenamiento que se enlaza a. El `szStatusText` proporciona el nombre para mostrar de la ubicación de datos.  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 La operación de enlace continúa recibiendo el objeto o el almacenamiento que se enlaza a. El `szStatusText` proporciona el nombre para mostrar de la ubicación de datos.  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 La operación de enlace ha terminado de recibir el objeto o el almacenamiento que se enlaza a. El `szStatusText` proporciona el nombre para mostrar de la ubicación de datos.  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 Una instancia del objeto que se enlaza a está a punto de crearse. El `szStatusText` proporciona el CLSID del nuevo objeto en formato de cadena, que permite al cliente una oportunidad cancelar la operación de enlace, si lo desea.  
  
##  <a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding  
 Reemplace esta función en sus clases derivadas para realizar acciones cuando el enlace se está iniciando.  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca de nuevo por el moniker. La implementación predeterminada no hace nada.  
  
##  <a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding  
 Llamado por el moniker al final de la operación de enlace.  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>Parámetros  
 `hresult`  
 Un `HRESULT` que es el error o un valor de advertencia.  
  
 *szErrort*  
 Una cadena de caracteres que describe el error.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para llevar a cabo acciones cuando se detiene la transferencia. De forma predeterminada, la función se libera `IBinding`.  
  
 Para obtener una descripción de la `IBinding` interfaz, vea el SDK de Windows.  
  
##  <a name="open"></a>CAsyncMonikerFile::Open  
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
 `lpszURL`  
 Un puntero al archivo que se abrió de forma asincrónica. El archivo puede ser cualquier dirección URL o el nombre de archivo válido.  
  
 `pError`  
 Un puntero a las excepciones del archivo. Si se produce un error, se establecerá la causa.  
  
 `pMoniker`  
 Un puntero a la interfaz de moniker asincrónico `IMoniker`, un moniker preciso que es la combinación del moniker del documento, que puede recuperar con **IOleClientSite::GetMoniker (** *OLEWHICHMK_ CONTENEDOR* **)**y un moniker creado a partir del nombre de ruta de acceso. El control puede utilizar este moniker para enlazar, pero esto no es el moniker que debe guardar el control.  
  
 *pBindHost*  
 Un puntero a la `IBindHost` interfaz que se usará para crear el moniker desde una ruta de acceso relativa potencialmente. Si el host de enlace no es válido o no proporciona un moniker, la llamada tiene como valor predeterminado **abiertos (** `lpszFileName` **,**`pError`**)**. Para obtener una descripción de la `IBindHost` interfaz, vea el SDK de Windows.  
  
 `pServiceProvider`  
 Puntero a la interfaz `IServiceProvider`. Si el proveedor de servicios no es válido o no proporciona el servicio para `IBindHost`, tiene como valor predeterminado de la llamada a **abiertos (** `lpszFileName` **,**`pError`**)**.  
  
 *pUnknown*  
 Un puntero a la **IUnknown** interfaz. Si `IServiceProvider` se encuentra, la función de consulta para `IBindHost`. Si el proveedor de servicios no es válido o no proporciona el servicio para `IBindHost`, tiene como valor predeterminado de la llamada a **abiertos (** `lpszFileName` **,**`pError`**)**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el archivo se abre correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada inicia el proceso de enlace.  
  
 Puede usar una dirección URL o un nombre de archivo para el `lpszURL` parámetro. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - O  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase de CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase de CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty (clase)](../../mfc/reference/cdatapathproperty-class.md)
