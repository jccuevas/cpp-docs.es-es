---
title: CDocument (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
dev_langs: C++
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dad4a2bb3da49b0163367761aeefe85384ecdfb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdocument-class"></a>CDocument (clase)
Proporciona la funcionalidad básica para las clases definidas por el usuario del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDocument : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument::CDocument](#cdocument)|Construye un objeto `CDocument`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument:: AddView](#addview)|Asocia una vista al documento.|  
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicializa la fragmentación lectura.|  
|[CDocument::CanCloseFrame](#cancloseframe)|Avanzada reemplazable; se llama antes de cerrar una ventana de marco ver este documento.|  
|[CDocument::ClearChunkList](#clearchunklist)|Borra la lista de fragmentos.|  
|[CDocument::ClearPathName](#clearpathname)|Borra la ruta de acceso del objeto de documento.|  
|[CDocument::DeleteContents](#deletecontents)|Se llama para realizar una limpieza del documento.|  
|[CDocument::FindChunk](#findchunk)|Busca un fragmento con el GUID especificado.|  
|[CDocument::GetAdapter](#getadapter)|Devuelve un puntero al objeto que implementa `IDocument` interfaz.|  
|[CDocument::GetDocTemplate](#getdoctemplate)|Devuelve un puntero a la plantilla de documento que describe el tipo del documento.|  
|[CDocument::GetFile](#getfile)|Devuelve un puntero a lo que se desea `CFile` objeto.|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Devuelve la posición del primer en la lista de vistas; se utiliza para iniciar la iteración.|  
|[CDocument::GetNextView](#getnextview)|Recorre en iteración la lista de vistas asociadas con el documento.|  
|[CDocument::GetPathName](#getpathname)|Devuelve la ruta de acceso del archivo de datos del documento.|  
|[CDocument::GetThumbnail](#getthumbnail)|Se llama para crear un mapa de bits para usarse por proveedor en miniatura para mostrar la vista en miniatura.|  
|[CDocument::GetTitle](#gettitle)|Devuelve el título del documento.|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Se llama para inicializar el contenido de búsqueda para buscar controlador.|  
|[CDocument::IsModified](#ismodified)|Indica si el documento se ha modificado desde que se guardó por última vez.|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indica si esta instancia de `CDocument` se creó el objeto de controlador de búsqueda & Organizar.|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Se llama para cargar los datos del documento de secuencia.|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Se llama antes de que se cambia la fuente de vista previa avanzada.|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|Se llama después de una vista se agrega o se quitan del documento.|  
|[CDocument::OnCloseDocument](#onclosedocument)|Se llama para cerrar el documento.|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Lo llama el marco cuando sea necesario crear un período de vista previa de vista previa avanzada.|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|Lo llama el marco de trabajo en respuesta a un evento de documento.|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Invalide este método en una clase derivada para dibujar el contenido de la vista en miniatura.|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Lo llama el marco cuando sea necesario cargar los datos del documento de flujo.|  
|[CDocument::OnNewDocument](#onnewdocument)|Se llama para crear un nuevo documento.|  
|[CDocument:: OnOpenDocument](#onopendocument)|Se llama para abrir un documento existente.|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Hace que el controlador de vista previa para devolver el HWND de la llamada a la función GetFocus.|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Hace que el controlador de vista previa para controlar una pulsación de tecla pasado a desde el suministro de mensajes del proceso en el que se ejecuta el controlador de vista previa.|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Se llama cuando ha cambiado el color de fondo de vista previa avanzada.|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Se llama cuando ha cambiado la fuente de vista previa avanzada.|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Se llama cuando ha cambiado el sitio de vista previa avanzada.|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Se llama cuando cambia el color del texto de vista previa avanzada.|  
|[CDocument::OnSaveDocument](#onsavedocument)|Se llama para guardar el documento en el disco.|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|Llamado por el marco de trabajo cuando se está descargando el controlador de vista previa.|  
|[CDocument::PreCloseFrame](#precloseframe)|Se llama antes de cerrar la ventana de marco.|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Lee el siguiente valor de fragmento.|  
|[CDocument::ReleaseFile](#releasefile)|Libera un archivo para que esté disponible para su uso por otras aplicaciones.|  
|[CDocument::RemoveChunk](#removechunk)|Quita un fragmento con el GUID especificado.|  
|[CDocument::RemoveView](#removeview)|Desasocia una vista del documento.|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Avanzada reemplazable; se llama cuando un abrir o guardar la operación no se puede completar debido a una excepción.|  
|[CDocument:: SaveModified](#savemodified)|Avanzada reemplazable; se llama para preguntar al usuario si se debe guardar el documento.|  
|[CDocument::SetChunkValue](#setchunkvalue)|Establece un valor de fragmento.|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Establece una marca que indica que ha modificado el documento desde que se guardó por última vez.|  
|[CDocument::SetPathName](#setpathname)|Establece la ruta de acceso del archivo de datos utilizado por el documento.|  
|[CDocument::SetTitle](#settitle)|Establece el título del documento.|  
|[UpdateAllViews](#updateallviews)|Notifica todas las vistas de documento se ha modificado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument:: OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo electrónico con el documento adjunto.|  
|[CDocument:: OnUpdateFileSendMail](#onupdatefilesendmail)|Habilita el comando Enviar correo si hay compatibilidad con el correo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Especifica que `CDocument` objeto fue creado por dllhost para las miniaturas. Se debe comprobar `CView::OnDraw`.|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Especifica que `CDocument` objeto fue creado por prevhost para `Rich Preview`. Se debe comprobar `CView::OnDraw`.|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|Especifica que `CDocument` objeto fue creado por el indizador u otra aplicación de búsqueda.|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Especifica el color de fondo de la ventana de vista previa avanzada. Este color se establece por host.|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Especifica el color de primer plano de la ventana de vista previa avanzada. Este color se establece por host.|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Especifica la fuente del texto en la ventana de vista previa avanzada. Esta información de fuentes se establece por host.|  
  
## <a name="remarks"></a>Comentarios  
 Un documento representa la unidad de datos que el usuario normalmente se abre con el comando Abrir archivo y lo guarda con el comando Archivo/Guardar.  
  
 **CDocument** admite operaciones estándares, como la creación de un documento, se cargan y guardarlo. El marco de trabajo manipula documentos mediante la interfaz definida por **CDocument**.  
  
 Una aplicación puede admitir más de un tipo de documento; Por ejemplo, una aplicación podría admitir hojas de cálculo y documentos de texto. Cada tipo de documento tiene una plantilla de documento asociado; la plantilla de documento especifica qué recursos (por ejemplo, tabla de aceleradores, icono o menú) se usan para ese tipo de documento. Cada documento contiene un puntero a su asociado `CDocTemplate` objeto.  
  
 Los usuarios interactúan con un documento a través de la [CView](../../mfc/reference/cview-class.md) objetos asociados a él. Una vista presenta una imagen del documento en una ventana de marco e interpreta proporcionados por el usuario que las operaciones en el documento. Un documento puede tener varias vistas asociadas a ella. Cuando el usuario abre una ventana en un documento, el marco de trabajo crea una vista y lo adjunta al documento. La plantilla de documento especifica qué tipo de ventana de vista y el marco se utilizan para mostrar cada tipo de documento.  
  
 Documentos forman parte del estándar del marco de trabajo enrutamiento de comandos y, por consiguiente, recibir comandos de componentes de la interfaz de usuario estándar (por ejemplo, el elemento de menú Guardar archivo). Un documento recibe comandos reenviados por la vista activa. Si el documento no controla un comando concreto, reenvía el comando a la plantilla de documento que lo administra.  
  
 Cuando se modifican los datos de un documento, cada una de sus vistas debe reflejar las modificaciones. **CDocument** proporciona el [UpdateAllViews](#updateallviews) función de miembro para notificar a las vistas de dichos cambios, por lo que las vistas pueden volver a dibujar por sí mismos según sea necesario. El marco de trabajo también le pedirá al usuario que guarde un archivo modificado antes de cerrarla.  
  
 Para implementar documentos en una aplicación típica, debe hacer lo siguiente:  
  
-   Derivar una clase de **CDocument** para cada tipo de documento.  
  
-   Agregue variables miembro para almacenar datos de cada documento.  
  
-   Implementar funciones de miembro para leer y modificar los datos del documento. Las vistas del documento son los usuarios más importantes de estas funciones de miembro.  
  
-   Invalidar el [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) función miembro en la clase de documento para escribir y leer los datos del documento hacia y desde el disco.  
  
 **CDocument** admite el envío de documentos a través de correo electrónico si hay compatibilidad de correo (MAPI). Consulte los artículos [MAPI](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
 Para obtener más información sobre **CDocument**, consulte [serialización](../../mfc/serialization-in-mfc.md), [temas sobre la arquitectura documento/vista](../../mfc/document-view-architecture.md), y [creación de documento/vista](../../mfc/document-view-creation.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="addview"></a>CDocument:: AddView  
 Llame a esta función para asociar una vista al documento.  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>Parámetros  
 `pView`  
 Señala a la vista que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función agrega la vista especificada a la lista de vistas asociadas con el documento; la función también establece el puntero de la vista documento a este documento. El marco de trabajo llama a esta función cuando se adjunta un objeto de vista recién creada para un documento; Esto se produce en respuesta a un comando nueva ventana, abrir archivo o archivo nuevo o cuando se divide una ventana divisora.  
  
 Llame a esta función solo si se crean manualmente o asociar una vista. Normalmente le permitirá que el marco de trabajo conectarse documentos y vistas mediante la definición de un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, la clase de vista y la clase de ventana de marco.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 Inicializa la fragmentación lectura.  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cancloseframe"></a>CDocument::CanCloseFrame  
 Llamado por el marco de trabajo antes de cerrar una ventana de marco mostrar el documento.  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFrame`  
 Apunta a la ventana de marco de una vista asociada al documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es seguro cerrar la ventana de marco; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada comprueba si hay otras ventanas de marco mostrar el documento. Si la ventana de marco especificado es el último que muestra el documento, la función pide al usuario que guarde el documento si se ha modificado. Reemplace esta función si desea realizar un procesamiento especial cuando se cierra una ventana de marco. Avanzada reemplazable.  
  
##  <a name="cdocument"></a>CDocument::CDocument  
 Construye un **CDocument** objeto.  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo controla la creación de documentos para usted. Invalidar el [OnNewDocument](#onnewdocument) función de miembro para realizar la inicialización en una base de cada documento; esto es especialmente importante en aplicaciones de único documento (SDI) de la interfaz.  
  
##  <a name="clearchunklist"></a>CDocument::ClearChunkList  
 Borra la lista de fragmentos.  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="clearpathname"></a>CDocument::ClearPathName  
 Borra la ruta de acceso del objeto de documento.  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>Comentarios  
 Borrar la ruta de acceso de un `CDocument` objeto hace que la aplicación solicitar al usuario cuando el documento se guarda a continuación. Esto hace que un **guardar** comandos se comportan como un **Guardar como** comando.  
  
##  <a name="deletecontents"></a>CDocument::DeleteContents  
 Lo llama el marco para eliminar los datos del documento sin destruir el **CDocument** propio objeto.  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>Comentarios  
 Se llama justo antes de que el documento es el encargado de destruirlo. También se denomina para asegurarse de que un documento está vacío antes de que se vuelve a usar. Esto es especialmente importante para una aplicación SDI, que usa un único documento; el documento se reutiliza siempre que el usuario crea o abre otro documento. Llame a esta función para implementar una "Editar borrar todo" o un comando similar que se elimina todos los datos del documento. La implementación predeterminada de esta función no hace nada. Reemplace esta función para eliminar los datos en el documento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="findchunk"></a>CDocument::FindChunk  
 Busca un fragmento con un GUID especificado.  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parámetros  
 `guid`  
 Especifica el GUID de un fragmento debe buscar.  
  
 `pid`  
 Especifica un PID de un fragmento para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Posición en la lista de fragmentos interno si se realiza correctamente. En caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getadapter"></a>CDocument::GetAdapter  
 Devuelve un puntero a un objeto que implementa el `IDocument` interfaz.  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un objeto que implementa el `IDocument` interfaz.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdoctemplate"></a>CDocument::GetDocTemplate  
 Llame a esta función para obtener un puntero a la plantilla de documento para este tipo de documento.  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla de documento para este tipo de documento, o **NULL** si el documento no está administrado por una plantilla de documento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="getfile"></a>CDocument::GetFile  
 Llame a esta función miembro para obtener un puntero a un `CFile` objeto.  
  
```  
virtual CFile* GetFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFileName`  
 Una cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta.  
  
 `pError`  
 Un puntero a un objeto de excepción de archivo existente que indica el estado de finalización de la operación.  
  
 `nOpenFlags`  
 Modo de acceso y uso compartido. Especifica la acción que se realizará al abrir el archivo. Puede combinar opciones que se muestran en el constructor de CFile [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) mediante el uso de la operación OR bit a bit (&#124;) operador. Permiso de acceso uno a y opción de un recurso compartido son necesarios; el **modeCreate** y **modeNoInherit** modos son opcionales.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CFile` objeto.  
  
##  <a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 Llame a esta función para obtener la posición de la primera vista en la lista de vistas asociadas con el documento.  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que puede utilizarse para la iteración con la [GetNextView](#getnextview) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getnextview"></a>CDocument::GetNextView  
 Llame a esta función para recorrer en iteración todas las vistas del documento.  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rPosition`  
 Una referencia a un **posición** valor devuelto por una llamada anterior a la `GetNextView` o [GetFirstViewPosition](#getfirstviewposition) funciones miembro. Este valor no debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la vista identificado por `rPosition`.  
  
### <a name="remarks"></a>Comentarios  
 La función devuelve la vista identificada por `rPosition` y, a continuación, establece `rPosition` a la **posición** valor de la vista siguiente en la lista. Si la vista recuperada es el último en la lista, a continuación, `rPosition` está establecido en **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getpathname"></a>CDocument::GetPathName  
 Llame a esta función para obtener la ruta de acceso completa del archivo de disco del documento.  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Ruta de acceso completa del documento. Esta cadena está vacía si el documento no se ha guardado o no tiene un archivo de disco asociado a él.  
  
##  <a name="getthumbnail"></a>CDocument::GetThumbnail  
 Crea un mapa de bits que se usa el proveedor en miniatura para mostrar la miniatura.  
  
```  
virtual BOOL GetThumbnail(
    UINT cx,  
    HBITMAP* phbmp,  
    DWORD* pdwAlpha);
```  
  
### <a name="parameters"></a>Parámetros  
 `cx`  
 Especifica el ancho y alto del mapa de bits.  
  
 `phbmp`  
 Contiene un identificador de un mapa de bits, cuando la función devuelve correctamente.  
  
 `pdwAlpha`  
 Contiene un valor de DWORD que especifica el valor de canal alfa, cuando la función devuelve correctamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si un mapa de bits para la miniatura se creó correctamente; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettitle"></a>CDocument::GetTitle  
 Llame a esta función para obtener el título del documento, que se deriva normalmente de nombre de archivo del documento.  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El título del documento.  
  
##  <a name="initializesearchcontent"></a>CDocument::InitializeSearchContent  
 Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para inicializar el contenido de búsqueda. El contenido debe ser una cadena con elementos delimitados por ";". Por ejemplo, "Seleccione; rectángulo; elemento OLE".  
  
##  <a name="ismodified"></a>CDocument::IsModified  
 Llame a esta función para determinar si el documento se ha modificado desde que se guardó por última vez.  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el documento se ha modificado desde que se guardó por última vez; en caso contrario es 0.  
  
##  <a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 Indica si esta instancia de `CDocument` se creó para el controlador de búsqueda & Organizar.  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si esta instancia de `CDocument` se creó para el controlador de búsqueda & Organizar.  
  
### <a name="remarks"></a>Comentarios  
 Actualmente, esta función devuelve `TRUE` solo para los controladores de vista previa avanzada que se implementa en un servidor fuera de proceso. Puede establecer las marcas adecuadas (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) en el nivel de aplicación para que esta función vuelva `TRUE`.  
  
##  <a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 Se llama para cargar los datos del documento desde una secuencia.  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 Un puntero a una secuencia. Esta secuencia es proporcionada por el comando de Shell.  
  
 `dwGrfMode`  
 Modo de acceso a la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si la operación de carga se realiza correctamente, en caso contrario HRESULT tiene un código de error.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar este método en una clase derivada para personalizar cómo cargar datos de la secuencia.  
  
##  <a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 Especifica que la `CDocument` objeto fue creado por dllhost para las miniaturas. Se debe comprobar `CView::OnDraw`.  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`indica que el documento se creó mediante dllhost para las miniaturas.  
  
##  <a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 Especifica que la `CDocument` objeto fue creado por prevhost de vista previa avanzada. Se debe comprobar `CView::OnDraw`.  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`indica que el documento se creó por prevhost de vista previa avanzada.  
  
##  <a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 Especifica que la `CDocument` se creó el objeto indizador u otra aplicación de búsqueda.  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`indica que se creó el documento indizador u otra aplicación de búsqueda.  
  
##  <a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 Especifica el color de fondo de la ventana de vista previa avanzada. Este color se establece por host.  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 Especifica el color de primer plano de la ventana de vista previa avanzada. Este color se establece por host.  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 Especifica la fuente del texto de la ventana de vista previa avanzada. Esta información de fuentes se establece por host.  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 Se llama antes de cambia la fuente de vista previa avanzada.  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onchangedviewlist"></a>CDocument::OnChangedViewList  
 Llamado por el marco de trabajo cuando se agrega una vista o se quitan del documento.  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función comprueba si la última vista se va a quitar y, si es así, elimina el documento. Reemplace esta función si desea realizar un procesamiento especial cuando el marco de trabajo agrega o quita una vista. Por ejemplo, si desea que un documento que permanecen abiertos, incluso cuando no hay ninguna vista asociada a él, invalide esta función.  
  
##  <a name="onclosedocument"></a>CDocument::OnCloseDocument  
 Llamado por el marco de trabajo cuando se cierra el documento, normalmente como parte del comando File Close.  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función destruye todos los fotogramas que se utiliza para ver el documento, se cierra la vista, limpia el contenido del documento y, a continuación, llama a la [DeleteContents](#deletecontents) para eliminar el documento de la función miembro datos.  
  
 Reemplace esta función si desea realizar la operación de limpieza especial cuando el marco de trabajo cierra un documento de procesamiento. Por ejemplo, si el documento representa un registro de una base de datos, puede que desee anular esta función para cerrar la base de datos. Debería llamar a la versión de la clase base de esta función de la invalidación.  
  
##  <a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 Lo llama el marco cuando sea necesario crear un período de vista previa de vista previa avanzada.  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si el marco se crea correctamente; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 Lo llama el marco de trabajo en respuesta a un evento de documento.  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `deEvent`  
 Un tipo de datos enumerado que describe el tipo de evento.  
  
### <a name="remarks"></a>Comentarios  
 Eventos de documento pueden afectar a varias clases. Este método es responsable de controlar los eventos de documento que afectan a las clases distinto de la [CDocument (clase)](../../mfc/reference/cdocument-class.md). Actualmente, la única clase que debe responder a eventos de documento es el [CDataRecoveryHandler clase](../../mfc/reference/cdatarecoveryhandler-class.md). El `CDocument` clase tiene otros métodos reemplazables responsables de controlar el efecto en el `CDocument`.  
  
 En la tabla siguiente se enumera los posibles valores para `deEvent` y los eventos que corresponden a.  
  
|Valor|Evento correspondiente|  
|-----------|-------------------------|  
|`onAfterNewDocument`|Se creó un nuevo documento.|  
|`onAfterOpenDocument`|Se abre un documento nuevo.|  
|`onAfterSaveDocument`|Se guardó el documento.|  
|`onAfterCloseDocument`|Se cerró el documento.|  
  
##  <a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
 Invalide este método en una clase derivada para dibujar la miniatura.  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>Parámetros  
 `dc`  
 Una referencia a un contexto de dispositivo.  
  
 `lprcBounds`  
 Especifica un rectángulo delimitador del área donde se debe dibujar la miniatura.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onfilesendmail"></a>CDocument:: OnFileSendMail  
 Envía un mensaje a través del host de correo electrónico residente (si existe) con el documento como datos adjuntos.  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>Comentarios  
 `OnFileSendMail`llamadas [OnSaveDocument](#onsavedocument) para serializar (documentos sin título y modificados en un archivo temporal, que se envía a través de correo electrónico Guardar). Si el documento no se ha modificado, no se necesita un archivo temporal; se envía el original. `OnFileSendMail`carga MAPI32. Archivo DLL si aún no se haya cargado.  
  
 Una implementación especial de `OnFileSendMail` para [COleDocument](../../mfc/reference/coledocument-class.md) archivos compuestos de identificadores correctamente.  
  
 **CDocument** admite el envío de documentos a través de correo electrónico si hay compatibilidad de correo (MAPI). Consulte los artículos [temas de MAPI](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 Lo llama el marco cuando sea necesario cargar los datos del documento desde una secuencia.  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 Un puntero a un flujo de entrada.  
  
 `grfMode`  
 Modo de acceso a la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si la carga se realiza correctamente; en caso contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onnewdocument"></a>CDocument::OnNewDocument  
 Lo llama el marco como parte del comando archivo nuevo.  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el documento se inicializó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función llama el [DeleteContents](#deletecontents) función de miembro para asegurarse de que el documento está vacío y, a continuación, marca el nuevo documento como limpio. Reemplace esta función para inicializar la estructura de datos para un nuevo documento. Debería llamar a la versión de la clase base de esta función de la invalidación.  
  
 Si el usuario elige el comando nuevo archivo en una aplicación SDI, el marco de trabajo usa esta función para reinicializar el documento existente, en lugar de crear uno nuevo. Si el usuario elige archivo nuevo en una aplicación de múltiples documentos (MDI) de la interfaz, el marco de trabajo cada vez que crea un nuevo documento y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización de esta función en lugar de en el constructor para el archivo nuevo comando sea efectivo en SDI (aplicaciones).  
  
 Tenga en cuenta que hay casos donde `OnNewDocument` se llama dos veces. Esto se produce cuando el documento se incrusta como un servidor de documentos ActiveX. Llama primero a la función la `CreateInstance` método (expuestos por el `COleObjectFactory`-clase derivada) y una segunda vez por la `InitNew` método (expuestos por el `COleServerDoc`-clase derivada).  
  
### <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran métodos alternativos para inicializar un objeto de documento.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="onopendocument"></a>CDocument:: OnOpenDocument  
 Lo llama el marco como parte del comando Abrir archivo.  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Apunta a la ruta de acceso del documento que se abran.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se cargó correctamente el documento; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función abre el archivo especificado, llamadas el [DeleteContents](#deletecontents) llama a la función miembro para asegurarse de que el documento está vacío, [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para leer el archivo contenido y, a continuación, marca el documento como limpio. Reemplace esta función si desea usar algo que no sea el mecanismo de almacenamiento o el archivo. Por ejemplo, puede escribir una aplicación, donde los documentos representan registros en una base de datos en lugar de en archivos independientes.  
  
 Si el usuario elige el comando Abrir archivo en una aplicación SDI, el marco de trabajo usa esta función para reinicializar existente **CDocument** objeto, en lugar de crear uno nuevo. Si el usuario elige abrir archivo en una aplicación MDI, el marco de trabajo construye un nuevo **CDocument** objeto cada vez y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización de esta función en lugar de en el constructor para el comando Abrir archivo sea efectiva en SDI (aplicaciones).  
  
### <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran métodos alternativos para inicializar un objeto de documento.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 Dirige el controlador de vista previa para volver a recupera el HWND de llamar al método el `GetFocus` función.  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `phwnd`  
 [out] Cuando este método vuelve, contiene un puntero para el HWND procedente de la llamada la `GetFocus` función de subproceso en primer plano del controlador de vista previa.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se realiza correctamente; o un valor de error en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 Hace que el controlador de vista previa para controlar una pulsación de tecla pasado a desde el suministro de mensajes del proceso en el que se ejecuta el controlador de vista previa.  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pmsg`  
 [in] Un puntero a un mensaje de ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el mensaje de pulsación de tecla puede ser procesado por el controlador de vista previa, el controlador lo procesa y devuelve S_OK. Si el controlador de vista previa no puede procesar el mensaje de pulsación de tecla, ofrece al host a través de `IPreviewHandlerFrame::TranslateAccelerator`. Si el host procesa el mensaje, este método devuelve S_OK. Si el host no procesa el mensaje, este método devuelve S_FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 Se llama cuando cambia el color de fondo de vista previa avanzada.  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 Se llama cuando cambia la fuente de vista previa avanzada.  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 Se llama cuando cambia el sitio de vista previa avanzada.  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 Se llama cuando cambia el color del texto de vista previa avanzada.  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsavedocument"></a>CDocument::OnSaveDocument  
 Lo llama el marco como parte del comando Archivo Guardar o guardar como.  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Señala a la ruta de acceso completa a la que se debe guardar el archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el documento se guardó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función abre el archivo especificado, llamadas [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para escribir los datos del documento en el archivo y, a continuación, las marcas del documento como limpiar. Reemplace esta función si desea realizar un procesamiento especial cuando el marco de trabajo guarda un documento. Por ejemplo, puede escribir una aplicación, donde los documentos representan registros en una base de datos en lugar de en archivos independientes.  
  
##  <a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 Lo llama el marco cuando el controlador de vista previa se descarga.  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onupdatefilesendmail"></a>CDocument:: OnUpdateFileSendMail  
 Habilita la **ID_FILE_SEND_MAIL** comando si está presente el soporte técnico de mail (MAPI).  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a la [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto asociado a la **ID_FILE_SEND_MAIL** comando.  
  
### <a name="remarks"></a>Comentarios  
 En caso contrario, la función quita el **ID_FILE_SEND_MAIL** comando en el menú, incluidos los separadores anteriores o por debajo del menú de elemento según corresponda. MAPI se habilita si MAPI32. DLL está presente en la ruta de acceso y, en la sección [correo electrónico] del archivo WIN. El archivo INI, MAPI = 1. Mayoría de las aplicaciones coloca este comando en el menú archivo.  
  
 **CDocument** admite el envío de documentos a través de correo electrónico si hay compatibilidad de correo (MAPI). Consulte los artículos [temas de MAPI](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="precloseframe"></a>CDocument::PreCloseFrame  
 El marco de trabajo llama a esta función miembro antes de que se destruya la ventana de marco.  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFrame`  
 Puntero a la [CFrameWnd](../../mfc/reference/cframewnd-class.md) que contiene el asociado **CDocument** objeto.  
  
### <a name="remarks"></a>Comentarios  
 Se puede invalidar para proporcionar la limpieza personalizada, pero no olvide llamar a la clase base también.  
  
 El valor predeterminado de `PreCloseFrame` no hace nada **CDocument**. El **CDocument**-las clases derivadas [COleDocument](../../mfc/reference/coledocument-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utilizar esta función miembro.  
  
##  <a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 Lee el siguiente valor de fragmento.  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppValue`  
 [out] Cuando la función devuelve, `ppValue` contiene el valor que se ha leído.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="releasefile"></a>CDocument::ReleaseFile  
 Esta función miembro se llama el marco de trabajo para la versión de un archivo, haciendo que esté disponible para su uso por otras aplicaciones.  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFile`  
 Un puntero al objeto CFile se libera.  
  
 `bAbort`  
 Especifica si el archivo es que se liberen utilizando `CFile::Close` o `CFile::Abort`. **FALSE** si el archivo es que se liberen mediante [CFile::Close](../../mfc/reference/cfile-class.md#close); **TRUE** si el archivo es que se liberen mediante [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="remarks"></a>Comentarios  
 Si `bAbort` es **TRUE**, `ReleaseFile` llamadas `CFile::Abort`, y se suelta el archivo. `CFile::Abort`no se iniciará una excepción.  
  
 Si `bAbort` es **FALSE**, `ReleaseFile` llamadas `CFile::Close` y el archivo se libera.  
  
 Reemplace esta función miembro para que requiera una intervención del usuario antes de que el archivo se libera.  
  
##  <a name="removechunk"></a>CDocument::RemoveChunk  
 Quita un fragmento con el GUID especificado.  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parámetros  
 `Guid`  
 Especifica el GUID de un fragmento va a quitar.  
  
 `Pid`  
 Especifica el PID de un fragmento va a quitar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removeview"></a>CDocument::RemoveView  
 Llame a esta función para separar una vista de un documento.  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>Parámetros  
 `pView`  
 Señala a la vista que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función quita la vista especificada en la lista de vistas asociadas con el documento; puntero al documento de la vista también establece en **NULL**. El marco de trabajo llama a esta función cuando se cierra una ventana de marco o se cierra un panel de una ventana divisora.  
  
 Llame a esta función solo si se separar manualmente una vista. Normalmente le permitirá que el marco de trabajo separar documentos y vistas mediante la definición de un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, la clase de vista y la clase de ventana de marco.  
  
 Vea el ejemplo en [AddView](#addview) para una implementación de ejemplo.  
  
##  <a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 Llama si se produce una excepción (normalmente un [CFileException](../../mfc/reference/cfileexception-class.md) o [CArchiveException](../../mfc/reference/carchiveexception-class.md)) al guardar o cargar el documento.  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Señala al nombre del documento que se va a guardar o cargar.  
  
 *e*  
 Apunta a la excepción que se produjo. Puede ser **NULL**.  
  
 *bSaving*  
 Marca que indica qué operación estaba en curso; es distinto de cero si el documento que se guardó, 0 si se está cargando el documento.  
  
 `nIDPDefault`  
 Identificador del mensaje de error que se mostrará si la función no especifica otro más específico.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada examina el objeto de excepción y se busca un mensaje de error que se describe específicamente la causa. Si no se encuentra un mensaje concreto o si *e* es **NULL**, el mensaje general especificado por el `nIDPDefault` se usa el parámetro. La función, a continuación, muestra un cuadro de mensaje que contiene el mensaje de error. Reemplace esta función si desea proporcionar mensajes de error personalizados adicionales. Avanzada reemplazable.  
  
##  <a name="savemodified"></a>CDocument:: SaveModified  
 Lo llama el marco antes de cerrar un documento modificado.  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es seguro continuar y cerrar el documento; 0 si no se debe cerrar el documento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función muestra un cuadro de mensaje que pide al usuario si desea guardar los cambios en el documento, si se ha efectuado alguno. Reemplace esta función si su programa requiere un procedimiento diferente de solicitud. Avanzada reemplazable.  
  
##  <a name="setchunkvalue"></a>CDocument::SetChunkValue  
 Establece un valor de fragmento.  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `pValue`  
 Especifica un valor de fragmento para establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 Llame a esta función una vez realizadas las modificaciones en el documento.  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bModified`  
 Marca que indica si se ha modificado el documento.  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a esta función de forma coherente, se asegura de que el marco de trabajo solicita al usuario guardar los cambios antes de cerrar un documento. Normalmente debe usar el valor predeterminado de **TRUE** para el `bModified` parámetro. Para marcar un documento como limpio (sin modificar), llame a esta función con un valor de **FALSE**.  
  
##  <a name="setpathname"></a>CDocument::SetPathName  
 Llame a esta función para especificar la ruta de acceso completa del archivo de disco del documento.  
  
```  
virtual void SetPathName(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Apunta a la cadena que se usará como la ruta de acceso para el documento.  
  
 `bAddToMRU`  
 Determina si el nombre de archivo se agrega a la mayoría de la archivos usados recientemente (MRU). Si **es TRUE,** se agrega el nombre de archivo; si **FALSE**, no se ha agregado.  
  
### <a name="remarks"></a>Comentarios  
 Dependiendo del valor de `bAddToMRU` es agregar la ruta de acceso o no agrega a la lista de elementos utilizados Recientemente mantenida por la aplicación. Tenga en cuenta que algunos documentos no están asociados a un archivo de disco. Llame a esta función solo si va a reemplazar la implementación predeterminada para abrir y guardar archivos utilizados por el marco de trabajo.  
  
##  <a name="settitle"></a>CDocument::SetTitle  
 Llame a esta función para especificar el título del documento (la cadena que se muestra en la barra de título de una ventana de marco).  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTitle`  
 Apunta a la cadena que se usará como el título del documento.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a esta función actualiza los títulos de todas las ventanas de marco del documento.  
  
##  <a name="updateallviews"></a>UpdateAllViews  
 Llame a esta función después de que se ha modificado el documento.  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSender`  
 Apunta a la vista que se modificó el documento, o **NULL** si todas las vistas que se van a actualizarse.  
  
 `lHint`  
 Contiene información sobre la modificación.  
  
 `pHint`  
 Apunta a un objeto que almacena información sobre la modificación.  
  
### <a name="remarks"></a>Comentarios  
 Debería llamar a esta función después de llamar a la [SetModifiedFlag](#setmodifiedflag) función miembro. Esta función le informa de cada vista asociada al documento, excepto para la vista especificada por `pSender`, que se ha modificado el documento. Se suele llamar a esta función de la clase de vista después de que el usuario ha cambiado el documento a través de una vista.  
  
 Esta función llama a la [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) ver la función miembro para cada una de las vistas del documento excepto el envío, pasar `pHint` y `lHint`. Use estos parámetros para pasar información a las vistas acerca de las modificaciones realizadas en el documento. Puede codificar información mediante `lHint` o puede definir un [CObject](../../mfc/reference/cobject-class.md)-clase derivada para almacenar información sobre las modificaciones y pasar un objeto de esa clase mediante `pHint`. Invalidar el `CView::OnUpdate` función miembro en su [CView](../../mfc/reference/cview-class.md)-clase derivada para optimizar la actualización de pantalla de la vista en función de la información que se pasa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Ejemplo SNAPVW de MFC](../../visual-cpp-samples.md)   
 [Ejemplo MFC NPP](../../visual-cpp-samples.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)
