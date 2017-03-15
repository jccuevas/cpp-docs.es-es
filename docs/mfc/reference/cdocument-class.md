---
title: CDocument (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocument
dev_langs:
- C++
helpviewer_keywords:
- documents [C++], serialization
- files [C++], documents
- command handling, documents and
- documents [C++], document classes
- documents [C++], multiple views
- serialization [C++], documents and
- CDocument class
- command routing, documents and
- views [C++], document
- documents [C++], command routing
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: 21
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
ms.openlocfilehash: 4d64b95f77139d984b855e710f3951434e489dd5
ms.lasthandoff: 02/24/2017

---
# <a name="cdocument-class"></a>CDocument (clase)
Proporciona la funcionalidad básica para las clases definidas por el usuario del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDocument : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocument::CDocument](#cdocument)|Construye un objeto `CDocument`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocument:: AddView](#addview)|Una vista se adjunta al documento.|  
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicializa fragmentos de lectura.|  
|[CDocument::CanCloseFrame](#cancloseframe)|Avanzada reemplazable; se llama antes de cerrar una ventana de marco viendo este documento.|  
|[CDocument::ClearChunkList](#clearchunklist)|Borra la lista de fragmentos.|  
|[CDocument::ClearPathName](#clearpathname)|Borra la ruta de acceso del objeto document.|  
|[CDocument::DeleteContents](#deletecontents)|Se llama para realizar la limpieza del documento.|  
|[CDocument::FindChunk](#findchunk)|Busca un fragmento con el GUID especificado.|  
|[CDocument::GetAdapter](#getadapter)|Devuelve un puntero al objeto que implementa `IDocument` interfaz.|  
|[CDocument::GetDocTemplate](#getdoctemplate)|Devuelve un puntero a la plantilla de documento que describe el tipo del documento.|  
|[CDocument::GetFile](#getfile)|Devuelve un puntero a la `CFile` objeto.|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Devuelve la posición de la primera en la lista de vistas; se utiliza para iniciar la iteración.|  
|[CDocument::GetNextView](#getnextview)|Recorre en iteración la lista de vistas asociadas con el documento.|  
|[CDocument::GetPathName](#getpathname)|Devuelve la ruta de acceso del archivo de datos del documento.|  
|[CDocument::GetThumbnail](#getthumbnail)|Se llama para crear un mapa de bits para usarse por el proveedor de miniaturas para mostrar la miniatura.|  
|[CDocument::GetTitle](#gettitle)|Devuelve el título del documento.|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.|  
|[CDocument::IsModified](#ismodified)|Indica si el documento se ha modificado desde que se guardó por última vez.|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indica si esta instancia de `CDocument` se creó el objeto para el controlador de organizar de aspecto de la búsqueda.|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Se llama para cargar datos de documentos de flujo.|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Se llama antes de que se cambia la fuente de vista previa avanzada.|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|Se llama después de una vista se agrega o se quita del documento.|  
|[CDocument::OnCloseDocument](#onclosedocument)|Se llama para cerrar el documento.|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Llamado por el marco cuando sea necesario crear un marco de vista previa para vista previa avanzada.|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|Llamado por el marco de trabajo en respuesta a un evento de documento.|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Invalide este método en una clase derivada para dibujar el contenido de la vista en miniatura.|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Llamado por el marco cuando sea necesario cargar los datos del documento de flujo.|  
|[CDocument::OnNewDocument](#onnewdocument)|Se llama para crear un nuevo documento.|  
|[CDocument:: OnOpenDocument](#onopendocument)|Se llama para abrir un documento existente.|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Indica el controlador de vista previa para devolver el HWND de la llamada a la función GetFocus.|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Indica el controlador de vista previa para controlar una pulsación de tecla que se pasan desde el suministro de mensajes del proceso en el que se ejecuta el controlador de vista previa.|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Se llama cuando ha cambiado el color de fondo de vista previa avanzada.|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Se llama cuando ha cambiado la fuente de vista previa avanzada.|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Se llama cuando ha cambiado el sitio de vista previa avanzada.|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Se llama cuando ha cambiado el color del texto de vista previa avanzada.|  
|[CDocument::OnSaveDocument](#onsavedocument)|Se llama para guardar el documento en el disco.|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|Llamado por el marco de trabajo cuando se está descargando el controlador de vista previa.|  
|[CDocument::PreCloseFrame](#precloseframe)|Se llama antes de cerrar la ventana de marco.|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Lee el siguiente valor de fragmento.|  
|[CDocument::ReleaseFile](#releasefile)|Libera un archivo para que esté disponible para su uso por otras aplicaciones.|  
|[CDocument::RemoveChunk](#removechunk)|Quita un fragmento con el GUID especificado.|  
|[CDocument::RemoveView](#removeview)|Desasocia una vista del documento.|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Avanzada reemplazable; llama al abrir o guardar la operación no se puede completar debido a una excepción.|  
|[CDocument:: SaveModified](#savemodified)|Avanzada reemplazable; se llama para preguntar al usuario si se debe guardar el documento.|  
|[CDocument::SetChunkValue](#setchunkvalue)|Establece un valor de fragmento.|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Establece una marca que indica que ha modificado el documento desde que se guardó por última vez.|  
|[CDocument::SetPathName](#setpathname)|Establece la ruta de acceso del archivo de datos utilizado por el documento.|  
|[CDocument::SetTitle](#settitle)|Establece el título del documento.|  
|[UpdateAllViews](#updateallviews)|Notifica todas las vistas de documento se ha modificado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocument:: OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo electrónico con el documento adjunto.|  
|[CDocument:: OnUpdateFileSendMail](#onupdatefilesendmail)|Si está presente, permite el comando Enviar correo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Especifica que `CDocument` objeto fue creado por dllhost para las miniaturas. Debe comprobarse `CView::OnDraw`.|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Especifica que `CDocument` objeto fue creado por prevhost para `Rich Preview`. Debe comprobarse `CView::OnDraw`.|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|Especifica que `CDocument` objeto fue creado por el indizador u otra aplicación de búsqueda.|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Especifica el color de fondo de la ventana de vista previa avanzada. Este color se establece por host.|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Especifica el color de primer plano de la ventana de vista previa avanzada. Este color se establece por host.|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Especifica la fuente del texto en la ventana de vista previa avanzada. Esta información de fuente se establece por host.|  
  
## <a name="remarks"></a>Comentarios  
 Un documento representa la unidad de datos que el usuario normalmente se abre con el comando Abrir archivo y guarda con el comando Guardar archivo.  
  
 **CDocument** admite operaciones estándares, como la creación de un documento, se cargan y guardarlo. El marco de trabajo manipula documentos mediante la interfaz definida por **CDocument**.  
  
 Una aplicación puede admitir más de un tipo de documento; Por ejemplo, una aplicación podría admitir hojas de cálculo y documentos de texto. Cada tipo de documento tiene una plantilla de documento asociado; la plantilla de documento especifica qué recursos (por ejemplo, tabla de aceleradores, icono o menú) se usan para ese tipo de documento. Cada documento contiene un puntero a su asociado `CDocTemplate` objeto.  
  
 Los usuarios interactúan con un documento a través de la [CView](../../mfc/reference/cview-class.md) objetos asociados a él. Una vista presenta una imagen del documento en una ventana de marco e interpreta proporcionados por el usuario como operaciones en el documento. Un documento puede tener varias vistas asociadas con él. Cuando el usuario abre una ventana en un documento, el marco de trabajo crea una vista y lo adjunta al documento. La plantilla de documento especifica qué tipo de ventana de vista y el marco se utilizan para mostrar cada tipo de documento.  
  
 Documentos forman parte del estándar del marco de trabajo enrutamiento de comandos y, por consiguiente, recibir comandos de componentes de interfaz de usuario estándar (por ejemplo, el elemento de menú Guardar archivo). Un documento recibe comandos reenviados por la vista activa. Si el documento no controla un comando determinado, reenvía el comando a la plantilla de documento que lo administra.  
  
 Cuando se modifican los datos de un documento, cada una de las vistas debe reflejar las modificaciones. **CDocument** proporciona el [UpdateAllViews](#updateallviews) función miembro para notificar a las vistas de dichos cambios, por lo que las vistas pueden dibujar según sea necesario. El marco también le pedirá al usuario que guarde un archivo modificado antes de cerrarla.  
  
 Para implementar los documentos en una aplicación típica, debe hacer lo siguiente:  
  
-   Derivar una clase de **CDocument** para cada tipo de documento.  
  
-   Agregue variables miembro para almacenar los datos de cada documento.  
  
-   Implementar funciones de miembro para leer y modificar los datos del documento. Las vistas del documento son los usuarios más importante de estas funciones miembro.  
  
-   Invalidar el [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) función miembro en la clase de documento para escribir y leer los datos del documento a y desde el disco.  
  
 **CDocument** admite enviar el documento a través de correo electrónico si hay compatibilidad de correo (MAPI). Consulte los artículos [MAPI](../../mfc/mapi.md) y [compatibilidad con MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
 Para obtener más información sobre **CDocument**, consulte [serialización](../../mfc/serialization-in-mfc.md), [temas sobre la arquitectura documento/vista](../../mfc/document-view-architecture.md), y [creación de documento/vista](../../mfc/document-view-creation.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameaddviewa--cdocumentaddview"></a><a name="addview"></a>CDocument:: AddView  
 Llame a esta función para asociar una vista al documento.  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>Parámetros  
 `pView`  
 Apunta a la vista que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función agrega la vista especificada a la lista de vistas asociadas con el documento; la función también establece el puntero de la vista documento a este documento. El marco de trabajo llama a esta función cuando se adjunta un objeto de vista recién creada para un documento. Esto se produce en respuesta a un comando nuevo archivo, abrir archivo o nueva ventana o cuando se divide una ventana divisora.  
  
 Llame a esta función sólo si está creando manualmente y asociar una vista. Normalmente le permitirá que el marco de trabajo conectarse documentos y vistas definiendo un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, la clase de vista y la clase de ventana de marco.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocViewSDI&#12;](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="a-namebeginreadchunksa--cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 Inicializa fragmentos de lectura.  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecancloseframea--cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument::CanCloseFrame  
 Llamado por el marco antes de cerrar una ventana de marco que muestra el documento.  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFrame`  
 Apunta a la ventana de marco de una vista asociada al documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si es seguro cerrar la ventana de marco; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada comprueba si hay otras ventanas de marco que muestra el documento. Si la ventana de marco especificado es el último que muestra el documento, la función pide al usuario que guarde el documento si se ha modificado. Reemplace esta función si desea realizar un procesamiento especial cuando se cierra una ventana de marco. Avanzada reemplazable.  
  
##  <a name="a-namecdocumenta--cdocumentcdocument"></a><a name="cdocument"></a>CDocument::CDocument  
 Construye un **CDocument** objeto.  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco controla la creación de documentos para usted. Invalidar el [OnNewDocument](#onnewdocument) función miembro para realizar la inicialización en una base por documento; esto es especialmente importante en aplicaciones de único documento (SDI) de la interfaz.  
  
##  <a name="a-nameclearchunklista--cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument::ClearChunkList  
 Borra la lista de fragmentos.  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameclearpathnamea--cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument::ClearPathName  
 Borra la ruta de acceso del objeto document.  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>Comentarios  
 Borrar la ruta de acceso de un `CDocument` objeto hace que la aplicación pedir al usuario cuando el documento se guarda a continuación. Esto hace que un **guardar** comandos se comportan como un **Guardar como** comando.  
  
##  <a name="a-namedeletecontentsa--cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::DeleteContents  
 Llamado por el marco para eliminar los datos del documento sin destruir la **CDocument** propio objeto.  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>Comentarios  
 Se llama justo antes de que el documento es para ser destruidos. También se le llama para asegurarse de que un documento está vacío antes de que se vuelve a utilizar. Esto es especialmente importante para una aplicación SDI, que utiliza un único documento. el documento se vuelve a utilizar cada vez que el usuario crea o abre otro documento. Llame a esta función para implementar un comando similar que elimine todos los datos del documento o "Editar borrar todo". La implementación predeterminada de esta función no hace nada. Reemplazar esta función para eliminar los datos en el documento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#57;](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="a-namefindchunka--cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::FindChunk  
 Busca un fragmento con un GUID especificado.  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parámetros  
 `guid`  
 Especifica el GUID de un fragmento que buscar.  
  
 `pid`  
 Especifica un PID de un fragmento para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Posición en la lista interna de fragmento si se realiza correctamente. De lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetadaptera--cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::GetAdapter  
 Devuelve un puntero a un objeto que implementa el `IDocument` interfaz.  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un objeto que implementa el `IDocument` interfaz.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdoctemplatea--cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::GetDocTemplate  
 Llame a esta función para obtener un puntero a la plantilla de documento para este tipo de documento.  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la plantilla de documento para este tipo de documento o **NULL** si el documento no está administrado por una plantilla de documento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#58;](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="a-namegetfilea--cdocumentgetfile"></a><a name="getfile"></a>CDocument::GetFile  
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
 Un puntero a un objeto de excepción de archivos existente que indica el estado de finalización de la operación.  
  
 `nOpenFlags`  
 Modo de acceso y uso compartido. Especifica la acción que se realizará al abrir el archivo. Puede combinar opciones que se muestran en el constructor de CFile [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) utilizando el operador OR bit a bit (|) (operador). Permiso de acceso y la opción de un recurso compartido son necesarios; el **modeCreate** y **modeNoInherit** modos son opcionales.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CFile` objeto.  
  
##  <a name="a-namegetfirstviewpositiona--cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 Llame a esta función para obtener la posición de la primera vista en la lista de vistas asociadas con el documento.  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **posición** valor que puede utilizarse para la iteración con la [GetNextView](#getnextview) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#59;](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="a-namegetnextviewa--cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::GetNextView  
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
 La función devuelve la vista identificada por `rPosition` y, a continuación, se establece `rPosition` a la **posición** valor de la vista siguiente en la lista. Si la vista recuperada es el último de la lista, `rPosition` está establecido en **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#59;](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="a-namegetpathnamea--cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::GetPathName  
 Llame a esta función para obtener la ruta de acceso completa del archivo de disco del documento.  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Ruta de acceso completa del documento. Esta cadena está vacía si el documento no se ha guardado o no tiene un archivo de disco asociado a él.  
  
##  <a name="a-namegetthumbnaila--cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::GetThumbnail  
 Crea un mapa de bits que utilizará el proveedor en miniatura para mostrar la miniatura.  
  
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
 Contiene un valor DWORD que especifica el valor de canal alfa, cuando la función devuelve correctamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si un mapa de bits para la miniatura se creó correctamente; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettitlea--cdocumentgettitle"></a><a name="gettitle"></a>CDocument::GetTitle  
 Llame a esta función para obtener el título del documento, que normalmente se deriva de un nombre de archivo del documento.  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El título del documento.  
  
##  <a name="a-nameinitializesearchcontenta--cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::InitializeSearchContent  
 Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para inicializar el contenido de la búsqueda. El contenido debe ser una cadena con elementos delimitados por ";". Por ejemplo, "punto; rectángulo; elemento OLE".  
  
##  <a name="a-nameismodifieda--cdocumentismodified"></a><a name="ismodified"></a>CDocument::IsModified  
 Llame a esta función para determinar si el documento se ha modificado desde que se guardó por última vez.  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el documento se ha modificado desde que se guardó por última vez; en caso contrario, 0.  
  
##  <a name="a-nameissearchandorganizehandlera--cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 Indica si esta instancia de `CDocument` se creó para el controlador de organizar de aspecto de la búsqueda.  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si esta instancia de `CDocument` se creó para el controlador de organizar de aspecto de la búsqueda.  
  
### <a name="remarks"></a>Comentarios  
 Actualmente, esta función devuelve `TRUE` sólo para controladores de vista previa avanzada implementados en un servidor fuera de proceso. Puede establecer las marcas apropiadas (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) en el nivel de aplicación para que esta función vuelva `TRUE`.  
  
##  <a name="a-nameloaddocumentfromstreama--cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 Se llama para cargar los datos de documentos desde una secuencia.  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 Puntero a una secuencia. Esta secuencia se suministra el shell.  
  
 `dwGrfMode`  
 Modo de acceso a la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si la operación de carga se realiza correctamente, en caso contrario HRESULT con un código de error.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar este método en una clase derivada para personalizar cómo cargar datos de la secuencia.  
  
##  <a name="a-namembgetthumbnailmodea--cdocumentmbgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 Especifica que la `CDocument` objeto fue creado por dllhost para las miniaturas. Debe comprobarse `CView::OnDraw`.  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`indica que el documento se creó con dllhost para las miniaturas.  
  
##  <a name="a-namembpreviewhandlermodea--cdocumentmbpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 Especifica que la `CDocument` objeto fue creado por prevhost de vista previa avanzada. Debe comprobarse `CView::OnDraw`.  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`indica que el documento se creó con prevhost de vista previa avanzada.  
  
##  <a name="a-namembsearchmodea--cdocumentmbsearchmode"></a><a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 Especifica que el `CDocument` se creó el objeto indizador u otra aplicación de búsqueda.  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`indica que se creó el documento indizador u otra aplicación de búsqueda.  
  
##  <a name="a-namemclrrichpreviewbackcolora--cdocumentmclrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 Especifica el color de fondo de la ventana de vista previa avanzada. Este color se establece por host.  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namemclrrichpreviewtextcolora--cdocumentmclrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 Especifica el color de primer plano de la ventana de vista previa avanzada. Este color se establece por host.  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namemlfrichpreviewfonta--cdocumentmlfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 Especifica la fuente del texto de la ventana de vista previa avanzada. Esta información de fuente se establece por host.  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonbeforerichpreviewfontchangeda--cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 Se llama antes de cambia la fuente de vista previa avanzada.  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonchangedviewlista--cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument::OnChangedViewList  
 Llamado por el marco de trabajo después de una vista se agrega o se quita del documento.  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función comprueba si se va a quitar la última vista y, si es así, elimina el documento. Reemplace esta función si desea realizar un procesamiento especial cuando el marco de trabajo agrega o quita una vista. Por ejemplo, si desea que un documento permanezcan abiertos, incluso cuando no hay ninguna vista asociada a él, reemplazar esta función.  
  
##  <a name="a-nameonclosedocumenta--cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument::OnCloseDocument  
 Lo llama el marco de trabajo cuando se cierra el documento, normalmente como parte del comando de cierre de archivo.  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función destruye todos los marcos que se utiliza para ver el documento, se cierra la vista, limpia el contenido del documento y, a continuación, llama a la [DeleteContents](#deletecontents) función miembro para eliminar los datos del documento.  
  
 Reemplace esta función si desea realizar el procesamiento de limpieza especial cuando el marco de trabajo cierra un documento. Por ejemplo, si el documento representa un registro en una base de datos, puede reemplazar esta función para cerrar la base de datos. La versión de la clase base de esta función se debe llamar desde el reemplazo.  
  
##  <a name="a-nameoncreatepreviewframea--cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 Llamado por el marco cuando sea necesario crear un marco de vista previa para vista previa avanzada.  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si el marco se ha creado correctamente; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondocumenteventa--cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 Llamado por el marco de trabajo en respuesta a un evento de documento.  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `deEvent`  
 Tipo de datos enumerado que describe el tipo de evento.  
  
### <a name="remarks"></a>Comentarios  
 Eventos de documento pueden afectar a varias clases. Este método es responsable de controlar los eventos de documento que afectan a las clases que no sea el [CDocument (clase)](../../mfc/reference/cdocument-class.md). Actualmente, la única clase que debe responder a eventos de documento es el [CDataRecoveryHandler clase](../../mfc/reference/cdatarecoveryhandler-class.md). El `CDocument` clase tiene otros métodos puede invalidar responsables de controlar el efecto en el `CDocument`.  
  
 La tabla siguiente enumeran los valores posibles de `deEvent` y los eventos que corresponden a.  
  
|Valor|Evento correspondiente|  
|-----------|-------------------------|  
|`onAfterNewDocument`|Se creó un nuevo documento.|  
|`onAfterOpenDocument`|Se abre un documento nuevo.|  
|`onAfterSaveDocument`|Se guardó el documento.|  
|`onAfterCloseDocument`|Se cerró el documento.|  
  
##  <a name="a-nameondrawthumbnaila--cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
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
  
##  <a name="a-nameonfilesendmaila--cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument:: OnFileSendMail  
 Envía un mensaje mediante el host de correo residente (si existe) con el documento como datos adjuntos.  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>Comentarios  
 `OnFileSendMail`llamadas [OnSaveDocument](#onsavedocument) para serializar (documentos sin título y modificados en un archivo temporal, que se enviará por correo electrónico Guardar). Si el documento no se ha modificado, no se necesita un archivo temporal; se envía el original. `OnFileSendMail`carga MAPI32. DLL si aún no se haya cargado.  
  
 Una implementación especial de `OnFileSendMail` de [COleDocument](../../mfc/reference/coledocument-class.md) archivos compuestos de identificadores correctamente.  
  
 **CDocument** admite enviar el documento a través de correo electrónico si hay compatibilidad de correo (MAPI). Consulte los artículos [MAPI temas](../../mfc/mapi.md) y [compatibilidad con MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="a-nameonloaddocumentfromstreama--cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 Llamado por el marco cuando sea necesario cargar los datos del documento desde una secuencia.  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 Puntero a un flujo de entrada.  
  
 `grfMode`  
 Modo de acceso a la secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si la carga se realiza correctamente; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonnewdocumenta--cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument::OnNewDocument  
 Llamado por el marco como parte del comando nuevo archivo.  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el documento se ha inicializado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función llama a la [DeleteContents](#deletecontents) función miembro para asegurarse de que el documento está vacío y, a continuación, marca el nuevo documento como limpio. Reemplazar esta función para inicializar la estructura de datos para un nuevo documento. La versión de la clase base de esta función se debe llamar desde el reemplazo.  
  
 Si el usuario elige el comando nuevo archivo en una aplicación SDI, el marco de trabajo usa esta función para reinicializar el documento existente, en lugar de crear uno nuevo. Si el usuario elige nuevo archivo en una aplicación de múltiples documentos (MDI) de la interfaz, el marco de trabajo cada vez que crea un nuevo documento y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización de esta función en lugar de en el constructor para el nuevo archivo comando sea efectivo en aplicaciones SDI.  
  
 Tenga en cuenta que hay casos donde `OnNewDocument` se llama dos veces. Esto ocurre cuando el documento se incrusta como un servidor de documentos ActiveX. Llama primero a la función de la `CreateInstance` (método) (expuestos por el `COleObjectFactory`-clase derivada) y una segunda vez por la `InitNew` (método) (expuestos por el `COleServerDoc`-clase derivada).  
  
### <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran métodos alternativos de inicializar un objeto de documento.  
  
 [!code-cpp[60 NVC_MFCDocView](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView&#61;](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView&#62;](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="a-nameonopendocumenta--cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument:: OnOpenDocument  
 Llamado por el marco como parte del comando Abrir archivo.  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Señala a la ruta de acceso del documento que se va a abrir.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el documento se ha cargado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función abre el archivo especificado, llamadas el [DeleteContents](#deletecontents) llama a la función miembro para asegurarse de que el documento está vacío, [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) leer el archivo de contenido y, a continuación, marca el documento como limpio. Reemplace esta función si desea utilizar algo que no sea el mecanismo de almacenamiento o el archivo. Por ejemplo, puede escribir una aplicación donde documentos representan registros en una base de datos en lugar de en archivos independientes.  
  
 Si el usuario elige el comando Abrir archivo en una aplicación SDI, el marco de trabajo usa esta función para reinicializar existente **CDocument** objeto, en lugar de crear uno nuevo. Si el usuario elige abrir archivo en una aplicación MDI, el marco de trabajo construye un nuevo **CDocument** objeto cada vez y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización de esta función en lugar de en el constructor para el comando Abrir archivo para ser eficaz en aplicaciones SDI.  
  
### <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran métodos alternativos de inicializar un objeto de documento.  
  
 [!code-cpp[60 NVC_MFCDocView](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView&#61;](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView&#62;](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView&#63;](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="a-nameonpreviewhandlerqueryfocusa--cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 Indica el controlador de vista previa para volver a recupera el HWND de llamar a la `GetFocus` (función).  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `phwnd`  
 [out] Cuando este método finaliza, contiene un puntero al HWND devuelve la llamada el `GetFocus` función de subproceso en primer plano del controlador de vista previa.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si es correcto; o un valor de error en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonpreviewhandlertranslateacceleratora--cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 Indica el controlador de vista previa para controlar una pulsación de tecla que se pasan desde el suministro de mensajes del proceso en el que se ejecuta el controlador de vista previa.  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pmsg`  
 [in] Puntero a un mensaje de ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el mensaje de pulsación de tecla puede ser procesado por el controlador de vista previa, el controlador lo procesa y devuelve S_OK. Si el controlador de vista previa no puede procesar el mensaje de pulsación de tecla, ofrece al host a través de `IPreviewHandlerFrame::TranslateAccelerator`. Si el host procesa el mensaje, este método devuelve S_OK. Si el host no procesa el mensaje, este método devuelve S_FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonrichpreviewbackcolorchangeda--cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 Se llama cuando ha cambiado el color de fondo de vista previa avanzada.  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonrichpreviewfontchangeda--cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 Se llama cuando ha cambiado la fuente de vista previa avanzada.  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonrichpreviewsitechangeda--cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 Se llama cuando ha cambiado el sitio de vista previa avanzada.  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonrichpreviewtextcolorchangeda--cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 Se llama cuando ha cambiado el color del texto de vista previa avanzada.  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonsavedocumenta--cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument::OnSaveDocument  
 Llamado por el marco como parte del comando Guardar archivo o guardar como.  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Señala a la ruta de acceso completa a la que se debe guardar el archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el documento se ha guardado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función abre el archivo especificado, llamadas [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para escribir los datos del documento en el archivo y, a continuación, las marcas del documento como limpiar. Reemplace esta función si desea realizar un procesamiento especial cuando el marco de trabajo guarda un documento. Por ejemplo, puede escribir una aplicación donde documentos representan registros en una base de datos en lugar de en archivos independientes.  
  
##  <a name="a-nameonunloadhandlera--cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 Llamado por el marco de trabajo cuando se descarga el controlador de vista previa.  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonupdatefilesendmaila--cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument:: OnUpdateFileSendMail  
 Habilita la **ID_FILE_SEND_MAIL** comando si está presente la compatibilidad de correo (MAPI).  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a la [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto asociado a la **ID_FILE_SEND_MAIL** comando.  
  
### <a name="remarks"></a>Comentarios  
 De lo contrario, la función quita la **ID_FILE_SEND_MAIL** comando desde el menú, incluidos los separadores anteriores o debajo del menú de elemento según corresponda. MAPI se habilita si MAPI32. DLL está presente en la ruta de acceso y, en la sección [correo electrónico] del archivo WIN. Archivo INI, MAPI =&1;. La mayoría de las aplicaciones colocan este comando en el menú archivo.  
  
 **CDocument** admite enviar el documento a través de correo electrónico si hay compatibilidad de correo (MAPI). Consulte los artículos [MAPI temas](../../mfc/mapi.md) y [compatibilidad con MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="a-nameprecloseframea--cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::PreCloseFrame  
 El marco de trabajo llama a esta función miembro antes de que se destruye la ventana de marco.  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFrame`  
 Puntero a la [CFrameWnd](../../mfc/reference/cframewnd-class.md) que contiene el asociado **CDocument** objeto.  
  
### <a name="remarks"></a>Comentarios  
 Se puede reemplazar para proporcionar limpieza personalizada, pero no olvide llamar a la clase base.  
  
 El valor predeterminado de `PreCloseFrame` no hace nada **CDocument**. El **CDocument**-clases derivadas [COleDocument](../../mfc/reference/coledocument-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utilizar esta función miembro.  
  
##  <a name="a-namereadnextchunkvaluea--cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 Lee el siguiente valor de fragmento.  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppValue`  
 [out] Devuelve la función `ppValue` contiene el valor que se ha leído.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namereleasefilea--cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::ReleaseFile  
 Esta función miembro se llama el marco de trabajo para la versión de un archivo, que están disponibles para su uso por otras aplicaciones.  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFile`  
 Un puntero al objeto CFile para liberarse.  
  
 `bAbort`  
 Especifica si el archivo es liberarse utilizando `CFile::Close` o `CFile::Abort`. **FALSE** si el archivo es liberarse mediante [CFile::Close](../../mfc/reference/cfile-class.md#close); **TRUE** si el archivo es liberarse mediante [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="remarks"></a>Comentarios  
 Si `bAbort` es **TRUE**, `ReleaseFile` llamadas `CFile::Abort`, y se libera el archivo. `CFile::Abort`no se producirá una excepción.  
  
 Si `bAbort` es **FALSE**, `ReleaseFile` llamadas `CFile::Close` y se libera el archivo.  
  
 Reemplace esta función miembro para requerir una acción del usuario antes de que se publique el archivo.  
  
##  <a name="a-nameremovechunka--cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::RemoveChunk  
 Quita un fragmento con el GUID especificado.  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parámetros  
 `Guid`  
 Especifica el GUID de un fragmento que se va a quitar.  
  
 `Pid`  
 Especifica el PID de un fragmento que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremoveviewa--cdocumentremoveview"></a><a name="removeview"></a>CDocument::RemoveView  
 Llame a esta función para separar una vista de un documento.  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>Parámetros  
 `pView`  
 Apunta a la vista que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función quita la vista especificada de la lista de vistas asociadas con el documento; puntero al documento de la vista también establece en **NULL**. El marco de trabajo llama a esta función cuando se cierra una ventana de marco o un panel de una ventana divisora está cerrado.  
  
 Llame a esta función sólo si manualmente se desasociar una vista. Normalmente le permitirá que el marco de separar los documentos y vistas mediante la definición de un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, la clase de vista y la clase de ventana de marco.  
  
 Consulte el ejemplo en [AddView](#addview) para una implementación de ejemplo.  
  
##  <a name="a-namereportsaveloadexceptiona--cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 Llamado si se produce una excepción (normalmente un [CFileException](../../mfc/reference/cfileexception-class.md) o [CArchiveException](../../mfc/reference/carchiveexception-class.md)) al guardar o cargar el documento.  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Señala al nombre del documento que se está guardando o cargando.  
  
 *e*  
 Señala a la excepción que se produjo. Puede ser **NULL**.  
  
 *bSaving*  
 Marca que indica qué operación estaba en curso; distinto de cero si el documento que se guardó, 0 si el documento que se cargó.  
  
 `nIDPDefault`  
 Identificador del mensaje de error que aparecerá si la función no especifica otro más específico.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada examina el objeto de excepción y busca un mensaje de error que describe concretamente la causa. Si no se encuentra un mensaje concreto o si *e* es **NULL**, el mensaje general especificado por el `nIDPDefault` se usa el parámetro. La función, a continuación, muestra un cuadro de mensaje que contiene el mensaje de error. Reemplace esta función si desea proporcionar mensajes de error personalizados adicionales. Avanzada reemplazable.  
  
##  <a name="a-namesavemodifieda--cdocumentsavemodified"></a><a name="savemodified"></a>CDocument:: SaveModified  
 Llamado por el marco antes de cerrar un documento modificado.  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si es seguro continuar y cerrar el documento. 0 si no se debe cerrar el documento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función muestra un cuadro de mensaje que pide al usuario si desea guardar los cambios en el documento, si se ha efectuado alguna. Reemplace esta función si su programa requiere un procedimiento diferente de solicitud. Avanzada reemplazable.  
  
##  <a name="a-namesetchunkvaluea--cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::SetChunkValue  
 Establece un valor de fragmento.  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `pValue`  
 Especifica que establezca un valor de fragmento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetmodifiedflaga--cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 Llame a esta función después de realizar modificaciones en el documento.  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bModified`  
 Marca que indica si se ha modificado el documento.  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a esta función de forma coherente, se asegura de que el marco de trabajo pide al usuario que guarde los cambios antes de cerrar un documento. Normalmente debe utilizar el valor predeterminado de **TRUE** para el `bModified` parámetro. Para marcar un documento limpio (sin modificar), llame a esta función con un valor de **FALSE**.  
  
##  <a name="a-namesetpathnamea--cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::SetPathName  
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
 Determina si el nombre de archivo se agrega a la mayoría de la archivos usados recientemente (MRU). Si **es TRUE,** se agrega el nombre de archivo; si **FALSE**, no se agrega.  
  
### <a name="remarks"></a>Comentarios  
 Dependiendo del valor de `bAddToMRU` es agregar la ruta de acceso o no agrega a la lista MRU mantenida por la aplicación. Tenga en cuenta que algunos documentos no están asociadas a un archivo de disco. Llame a esta función sólo si se va a reemplazar la implementación predeterminada para abrir y guardar archivos utilizados por el marco de trabajo.  
  
##  <a name="a-namesettitlea--cdocumentsettitle"></a><a name="settitle"></a>CDocument::SetTitle  
 Llame a esta función para especificar el título del documento (la cadena que se muestra en la barra de título de una ventana de marco).  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTitle`  
 Apunta a la cadena que se usará como el título del documento.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a esta función actualiza los títulos de todas las ventanas de marco del documento.  
  
##  <a name="a-nameupdateallviewsa--cdocumentupdateallviews"></a><a name="updateallviews"></a>UpdateAllViews  
 Llame a esta función una vez que se ha modificado el documento.  
  
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
 Contiene información acerca de la modificación.  
  
 `pHint`  
 Apunta a un objeto que almacena información sobre la modificación.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a esta función después de llamar a la [SetModifiedFlag](#setmodifiedflag) función miembro. Esta función le informa de cada vista adjuntado al documento, excepto para la vista especificada por `pSender`, que se ha modificado el documento. Se suele llamar a esta función desde la clase de vista después de que el usuario ha cambiado el documento a través de una vista.  
  
 Esta función llama a la [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) ver la función miembro para cada una de las vistas del documento excepto el envío, pasando `pHint` y `lHint`. Use estos parámetros para pasar información a las vistas acerca de las modificaciones realizadas en el documento. Puede codificar información mediante `lHint` o puede definir un [CObject](../../mfc/reference/cobject-class.md)-clase derivada para almacenar información sobre las modificaciones y pasar un objeto de esa clase utilizando `pHint`. Invalidar el `CView::OnUpdate` función miembro en su [CView](../../mfc/reference/cview-class.md)-clase derivada para optimizar la actualización de pantalla de la vista según la información que se pasa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#64;](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDIDOCVW de MFC](../../visual-cpp-samples.md)   
 [Ejemplo de MFC SNAPVW](../../visual-cpp-samples.md)   
 [Ejemplo de MFC NPP](../../visual-cpp-samples.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)

