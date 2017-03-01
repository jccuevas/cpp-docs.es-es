---
title: Clase CAsyncMonikerFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAsyncMonikerFile
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- OLE controls [C++], asynchronous
- monikers [C++], MFC
- asynchronous controls [C++]
- CAsyncMonikerFile class
- IMoniker interface, binding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: eb8727e6fe884c98fe010beab072fb7268f2e2c4
ms.lasthandoff: 02/24/2017

---
# <a name="casyncmonikerfile-class"></a>Clase CAsyncMonikerFile
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
|[CAsyncMonikerFile::Close](#close)|Cierra y libera todos los recursos.|  
|[CAsyncMonikerFile::GetBinding](#getbinding)|Recupera un puntero a la transferencia asincrónica de enlace.|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Recupera el formato de los datos de la secuencia.|  
|[CAsyncMonikerFile::Open](#open)|Abre un archivo de forma asincrónica.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Crea un objeto COM que implementa `IBindStatusCallback`.|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Llama a la biblioteca del sistema OLE para solicitar información sobre el tipo de enlace que se va a crear.|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|Llama a la biblioteca del sistema OLE para obtener la prioridad del enlace.|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a medida que estén disponible para el cliente durante las operaciones de enlace asincrónico.|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Se llama cuando hay pocos recursos.|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|Se llama para indicar el progreso en el proceso de transferencia de datos.|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Se llama cuando el enlace se está iniciando.|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia asincrónica.|  
  
## <a name="remarks"></a>Comentarios  
 Deriva de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), que a su vez se deriva de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` utiliza la [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) interfaz para tener acceso a cualquier flujo de datos de forma asincrónica, incluidos cargar archivos de forma asincrónica desde una dirección URL. Los archivos pueden ser propiedades de ruta de datos de los controles ActiveX.  
  
 Monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario con capacidad de respuesta durante las transferencias de archivos. Un buen ejemplo de esto es el uso de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas de los controles ActiveX. La `CDataPathProperty` objeto obtendrá repetidamente una devolución de llamada para indicar la disponibilidad de nuevos datos durante un proceso de exchange de propiedades largas.  
  
 Para obtener más información acerca de cómo utilizar controles ActiveX y monikers asincrónicos en aplicaciones de Internet, consulte los artículos siguientes:  
  
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
  
##  <a name="a-namecasyncmonikerfilea--casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile  
 Construye un objeto `CAsyncMonikerFile`.  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>Comentarios  
 No se crea el `IBindHost` interfaz. `IBindHost`se usa únicamente si se proporcionan en el **abiertos** función miembro.  
  
 Para obtener una descripción de la `IBindHost` , vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameclosea--casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Close  
 Llame a esta función para cerrar y liberar todos los recursos.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede llamar en archivos no abiertos o cerrados ya.  
  
##  <a name="a-namecreatebindstatuscallbacka--casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback  
 Crea un objeto COM que implementa `IBindStatusCallback`.  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkControlling`  
 Un puntero a desconocido de control (el exterior **IUnknown**) o **NULL** si no se utiliza la agregación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si `pUnkControlling` no **NULL**, la función devuelve un puntero al interno **IUnknown** en un nuevo objeto COM admitidos `IBindStatusCallback`. Si `pUnkControlling` es **NULL**, la función devuelve un puntero a un **IUnknown** en un nuevo objeto COM admitidos `IBindStatusCallback`.  
  
### <a name="remarks"></a>Comentarios  
 `CAsyncMonikerFile`requiere un objeto COM que implementa `IBindStatusCallback`. MFC implementa este tipo de objeto y es agregable. Puede reemplazar `CreateBindStatusCallback` para devolver su propio objeto COM. El objeto COM puede agregar la implementación de MFC mediante una llamada a `CreateBindStatusCallback` con el control desconocido del objeto COM. Objetos COM implementados mediante el `CCmdTarget` compatibilidad con COM puede recuperar el control utilizando desconocido **CCmdTarget::GetControllingUnknown**.  
  
 Como alternativa, puede delegar el objeto COM para la implementación de MFC mediante una llamada a **CreateBindStatusCallback (NULL)**.  
  
 [CAsyncMonikerFile::Open](#open) llamadas `CreateBindStatusCallback`.  
  
 Para obtener más información sobre el enlace asincrónico y monikers asincrónicos, vea el [IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060) interfaz y [enlace de forma asincrónica y el trabajo de almacenamiento](http://msdn.microsoft.com/library/windows/desktop/aa379152). Para obtener una explicación de la agregación, vea [agregaciones](http://msdn.microsoft.com/library/windows/desktop/ms686558). Todos los tres temas están en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetbindinfoa--casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo  
 Llamar desde el cliente de un moniker asincrónico para indicar que el moniker asincrónico cómo quiere enlazar.  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera la configuración de **IBindStatusCallBack**. Para obtener una descripción de la `IBindStatusCallback` , vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada establece el enlace sea asincrónico, utilizar un medio de almacenamiento (una secuencia) y utilizar el modelo de inserción de datos. Reemplace esta función si desea cambiar el comportamiento del enlace.  
  
 Una razón para hacerlo sería enlazar mediante el modelo de extracción de datos en lugar del modelo de inserción de datos. En un modelo de extracción de datos, el cliente de las unidades de la operación de enlace y el moniker sólo proporciona datos para el cliente cuando se leen. En un modelo de inserción de datos, el moniker de unidades de la operación de enlace asincrónico y continuamente notifica al cliente cada vez que hay nuevos datos disponibles.  
  
##  <a name="a-namegetbindinga--casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMonikerFile::GetBinding  
 Llame a esta función para recuperar un puntero a la transferencia asincrónica de enlace.  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `IBinding` interfaz proporcionada cuando comienza la transferencia asincrónica. Devuelve **NULL** si por algún motivo la transferencia no puede realizarse de manera asincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite controlar la transferencia de datos proceso a través de la `IBinding` de la interfaz, por ejemplo, con **IBinding::Abort**, **IBinding::Pause**, y **IBinding::Resume**.  
  
 Para obtener una descripción de la `IBinding` , vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetformatetca--casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc  
 Llame a esta función para recuperar el formato de los datos de la secuencia.  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la estructura de Windows [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) para la secuencia abierta actualmente. Devuelve **NULL** si el moniker no se ha enlazado, si no es asincrónica, o si no ha comenzado la operación asincrónica.  
  
##  <a name="a-namegetprioritya--casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority  
 Llamado desde el cliente de un moniker asincrónico inicia el proceso de enlace recibir la prioridad asignada al subproceso de la operación de enlace.  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La prioridad en el que llevará a cabo la transferencia asincrónica. Uno de los indicadores de prioridad de subprocesos estándar: **THREAD_PRIORITY_ABOVE_NORMAL**, **THREAD_PRIORITY_BELOW_NORMAL**, **THREAD_PRIORITY_HIGHEST**, **THREAD_PRIORITY_IDLE**, **THREAD_PRIORITY_LOWEST**, **THREAD_PRIORITY_NORMAL**, y **THREAD_PRIORITY_TIME_CRITICAL**. Vea la función de Windows [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) para obtener una descripción de estos valores.  
  
### <a name="remarks"></a>Comentarios  
 `GetPriority`no se debe llamar directamente. **THREAD_PRIORITY_NORMAL** devuelto por la implementación predeterminada.  
  
##  <a name="a-nameondataavailablea--casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable  
 Un moniker asincrónico llama `OnDataAvailable` para proporcionar datos al cliente cuando esté disponible, asincrónica durante el enlace de operaciones.  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwSize`  
 La cantidad acumulativa (en bytes) de los datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante para la operación o que no hay una cantidad específica está disponible.  
  
 *bscfFlag*  
 Un **BSCF** valor de enumeración. Puede ser uno o varios de los siguientes valores:  
  
- **BSCF_FIRSTDATANOTIFICATION** identifica la primera llamada a `OnDataAvailable` para una operación de enlace determinada.  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION** identifica una llamada intermedia a `OnDataAvailable` para una operación de enlace.  
  
- **BSCF_LASTDATANOTIFICATION** identifica la última llamada a `OnDataAvailable` para una operación de enlace.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Vea el ejemplo siguiente de una implementación de ejemplo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWinInet&#5;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="a-nameonlowresourcea--casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource  
 Llamado por el moniker cuando hay pocos recursos.  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `GetBinding( )-> Abort( )`.  
  
##  <a name="a-nameonprogressa--casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress  
 Llamado por el moniker repetidamente para indicar el progreso actual de esta operación de enlace, normalmente a intervalos razonables durante una operación larga.  
  
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
 Proporciona información adicional sobre el progreso de la operación de enlace. Los valores válidos proceden de la `BINDSTATUS` (enumeración). Para los valores posibles, vea la sección Comentarios.  
  
 `szStatusText`  
 Información sobre el progreso actual, dependiendo del valor de `ulStatusCode`. Para los valores posibles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Valores posibles de `ulStatusCode` (y `szStatusText` por cada valor) son:  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 Detecta el recurso que contiene el objeto o almacenamiento que se enlaza a la operación de enlace. El `szStatusText` proporciona el nombre para mostrar del recurso que se busca para (por ejemplo, "www.microsoft.com").  
  
 **BINDSTATUS_CONNECTING**  
 La operación de enlace se conecta al recurso que contiene el objeto o almacenamiento que se enlaza a. El `szStatusText` proporciona el nombre para mostrar del recurso que se está conectado a (por ejemplo, una dirección IP).  
  
 **BINDSTATUS_SENDINGREQUEST**  
 La operación de enlace está solicitando el objeto o almacenamiento que se enlaza a. El `szStatusText` proporciona el nombre para mostrar del objeto (por ejemplo, un nombre de archivo).  
  
 **BINDSTATUS_REDIRECTING**  
 La operación de enlace se ha redirigido a una ubicación de datos diferente. El `szStatusText` proporciona el nombre para mostrar de la nueva ubicación de datos.  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 La operación de enlace que recupere el objeto solicitado o almacenamiento de una copia en caché. The `szStatusText` is **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 La operación de enlace ha comenzado a recibir el objeto o almacenamiento que se enlaza a. El `szStatusText` proporciona el nombre para mostrar del almacén de datos.  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 La operación de enlace continúa recibiendo el objeto o almacenamiento que se enlaza a. El `szStatusText` proporciona el nombre para mostrar del almacén de datos.  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 Ha terminado de recibir el objeto o almacenamiento que se enlaza a la operación de enlace. El `szStatusText` proporciona el nombre para mostrar del almacén de datos.  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 Una instancia del objeto que se enlaza a está a punto de crearse. El `szStatusText` proporciona el CLSID del nuevo objeto en formato de cadena, lo que permite al cliente una oportunidad de cancelar la operación de enlace, si lo desea.  
  
##  <a name="a-nameonstartbindinga--casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding  
 Reemplace esta función en sus clases derivadas para realizar acciones cuando el enlace se está iniciando.  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca de nuevo por el moniker. La implementación predeterminada no hace nada.  
  
##  <a name="a-nameonstopbindinga--casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding  
 Llamado por el moniker al final de la operación de enlace.  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>Parámetros  
 `hresult`  
 Un `HRESULT` que es el error o advertencia.  
  
 *szErrort*  
 Una cadena de caracteres que describe el error.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para realizar acciones cuando se detiene la transferencia. De forma predeterminada, la función libera `IBinding`.  
  
 Para obtener una descripción de la `IBinding` , vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameopena--casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Open  
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
 Puntero al archivo que se abrió de forma asincrónica. El archivo puede ser cualquier dirección URL o el nombre de archivo válido.  
  
 `pError`  
 Puntero a las excepciones del archivo. En caso de error, se establecerá la causa del problema.  
  
 `pMoniker`  
 Un puntero a la interfaz de moniker asincrónico `IMoniker`, un moniker preciso que es la combinación del moniker del documento, que se puede recuperar con **IOleClientSite::GetMoniker (** *OLEWHICHMK_CONTAINER* **)**y un moniker creado a partir del nombre de ruta de acceso. El control puede utilizar este moniker para enlazar, pero esto no es el moniker que debe guardar el control.  
  
 *pBindHost*  
 Un puntero a la `IBindHost` interfaz que se usará para crear el moniker de una ruta de acceso potencialmente relativa. Si el host de enlace no es válido o no se proporciona un moniker, valores predeterminados de la llamada a **abiertos (** `lpszFileName` **,**`pError`**)**. Para obtener una descripción de la `IBindHost` , vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `pServiceProvider`  
 Puntero a la interfaz `IServiceProvider`. Si el proveedor de servicios no es válido o no proporciona el servicio para `IBindHost`, valores predeterminados de la llamada a **abiertos (** `lpszFileName` **,**`pError`**)**.  
  
 *pUnknown*  
 Un puntero a la **IUnknown** interfaz. Si `IServiceProvider` se encuentra la función de consulta para `IBindHost`. Si el proveedor de servicios no es válido o no proporciona el servicio para `IBindHost`, valores predeterminados de la llamada a **abiertos (** `lpszFileName` **,**`pError`**)**.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el archivo se abre correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada inicia el proceso de enlace.  
  
 Puede utilizar una dirección URL o un nombre de archivo para el `lpszURL` parámetro. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWinInet Nº&6;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 -O bien-  
  
 [!code-cpp[NVC_MFCWinInet&#7;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase de CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase de CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [Clase CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

