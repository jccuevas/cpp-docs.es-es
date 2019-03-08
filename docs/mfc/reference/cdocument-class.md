---
title: CDocument (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: b7358c2206c15660b9ffb283802283ee71e57f03
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299080"
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
|[CDocument::AddView](#addview)|Una vista se adjunta al documento.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicializa fragmentos de lectura.|
|[CDocument::CanCloseFrame](#cancloseframe)|Avanzada que se puede invalidar; se llama antes de cerrar una ventana de marco viendo en este documento.|
|[CDocument::ClearChunkList](#clearchunklist)|Borra la lista de fragmentos.|
|[CDocument::ClearPathName](#clearpathname)|Borra la ruta de acceso del objeto de documento.|
|[CDocument::DeleteContents](#deletecontents)|Se llama para realizar la limpieza del documento.|
|[CDocument::FindChunk](#findchunk)|Busca un fragmento con el GUID especificado.|
|[CDocument::GetAdapter](#getadapter)|Devuelve un puntero al objeto que implementa `IDocument` interfaz.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Devuelve un puntero a la plantilla de documento que describe el tipo del documento.|
|[CDocument::GetFile](#getfile)|Devuelve un puntero al deseado `CFile` objeto.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Devuelve la posición del primer en la lista de vistas; se utiliza para iniciar la iteración.|
|[CDocument::GetNextView](#getnextview)|Recorre en iteración la lista de las vistas asociadas al documento.|
|[CDocument::GetPathName](#getpathname)|Devuelve la ruta de acceso del archivo de datos del documento.|
|[CDocument::GetThumbnail](#getthumbnail)|Se llama para crear un mapa de bits que se usará el proveedor en miniatura para mostrar la miniatura.|
|[CDocument::GetTitle](#gettitle)|Devuelve el título del documento.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.|
|[CDocument::IsModified](#ismodified)|Indica si el documento se ha modificado desde que se guardó por última vez.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indica si esta instancia de `CDocument` se creó el objeto de controlador de búsqueda & Organizar.|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Se llama para cargar datos de documentos de flujo.|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Se llama antes de que se cambia la fuente de vista previa avanzada.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Se llama después de una vista se agrega o se quitan del documento.|
|[CDocument::OnCloseDocument](#onclosedocument)|Se llama para cerrar el documento.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Lo llama el marco de trabajo cuando es necesario crear un fotograma de vista previa para vista previa avanzada.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Lo llama el marco de trabajo en respuesta a un evento de documento.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Invalide este método en una clase derivada para dibujar el contenido de vista en miniatura.|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Lo llama el marco de trabajo cuando es necesario cargar los datos del documento de flujo.|
|[CDocument::OnNewDocument](#onnewdocument)|Se llama para crear un nuevo documento.|
|[CDocument::OnOpenDocument](#onopendocument)|Se llama para abrir un documento existente.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Dirige el controlador de vista previa para devolver el HWND de la llamada a la función GetFocus.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Dirige el controlador de vista previa para controlar una pulsación de tecla Subir de nivel de la bomba de mensaje del proceso en el que se está ejecutando el controlador de vista previa.|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Se llama cuando ha cambiado el color de fondo de vista previa avanzada.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Se llama cuando ha cambiado la fuente de vista previa avanzada.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Se llama cuando ha cambiado el sitio de vista previa avanzada.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Se llama cuando ha cambiado el color del texto de vista previa avanzada.|
|[CDocument::OnSaveDocument](#onsavedocument)|Se llama para guardar el documento en el disco.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Lo llama el marco de trabajo cuando se está descargando el controlador de vista previa.|
|[CDocument::PreCloseFrame](#precloseframe)|Se llama antes de cerrar la ventana de marco.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Lee el siguiente valor de fragmento.|
|[CDocument::ReleaseFile](#releasefile)|Libera un archivo para que esté disponible para su uso por otras aplicaciones.|
|[CDocument::RemoveChunk](#removechunk)|Quita un fragmento con el GUID especificado.|
|[CDocument::RemoveView](#removeview)|Desasocia una vista del documento.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Avanzada que se puede invalidar; se llama cuando una abierta o la operación de guardado no se puede completar debido a una excepción.|
|[CDocument::SaveModified](#savemodified)|Avanzada que se puede invalidar; se llama para preguntar al usuario si se debe guardar el documento.|
|[CDocument::SetChunkValue](#setchunkvalue)|Establece un valor de fragmento.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Establece una marca que indica que ha modificado el documento desde que se guardó por última vez.|
|[CDocument::SetPathName](#setpathname)|Establece la ruta de acceso del archivo de datos utilizado por el documento.|
|[CDocument::SetTitle](#settitle)|Establece el título del documento.|
|[CDocument::UpdateAllViews](#updateallviews)|Notifica a todas las vistas de ese documento se ha modificado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo electrónico con el documento adjunto.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Habilita el comando Enviar correo si el correo electrónico está presente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Especifica que `CDocument` objeto fue creado por dllhost para las miniaturas. Debe activarse en `CView::OnDraw`.|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Especifica que `CDocument` objeto fue creado por prevhost para `Rich Preview`. Debe activarse en `CView::OnDraw`.|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Especifica que `CDocument` objeto fue creado por el indexador u otra aplicación de búsqueda.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Especifica el color de fondo de ventana de vista previa avanzada. Este color se establece por host.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Especifica el color de primer plano de la ventana de vista previa avanzada. Este color se establece por host.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Especifica la fuente del texto en la ventana de vista previa avanzada. Esta información de fuente se establece por host.|

## <a name="remarks"></a>Comentarios

Un documento representa la unidad de datos que el usuario normalmente se abre con el comando Abrir archivo y guarda con el comando Guardar archivo.

`CDocument` admite operaciones estándares, como la creación de un documento, carga y lo guarda. El marco de trabajo manipula documentos mediante la interfaz definida por `CDocument`.

Una aplicación puede admitir más de un tipo de documento; Por ejemplo, una aplicación podría admitir hojas de cálculo y documentos de texto. Cada tipo de documento tiene una plantilla de documento asociado; la plantilla de documento especifica qué recursos (por ejemplo, tabla de aceleradores, icono o menú) se usan para ese tipo de documento. Cada documento contiene un puntero a su asociado `CDocTemplate` objeto.

Los usuarios interactúan con un documento a través de la [CView](../../mfc/reference/cview-class.md) objetos asociados con él. Una vista presenta una imagen del documento en una ventana de marco e interpreta la entrada del usuario que las operaciones en el documento. Un documento puede tener varias vistas asociadas con él. Cuando el usuario abre una ventana en un documento, el marco de trabajo crea una vista y lo adjunta al documento. La plantilla de documento especifica qué tipo de vista y el marco de ventana se usan para mostrar de cada tipo de documento.

Documentos forman parte del estándar de .NET framework enrutamiento de comandos y por consiguiente reciben comandos de componentes de interfaz de usuario estándar (por ejemplo, el elemento de menú Guardar archivo). Un documento recibe comandos reenviados por la vista activa. Si el documento no controla un comando determinado, reenvía el comando a la plantilla de documento que lo administra.

Cuando se modifican los datos de un documento, cada uno de sus vistas debe reflejar las modificaciones. `CDocument` proporciona el [UpdateAllViews](#updateallviews) función miembro para notificar a las vistas de dichos cambios, por lo que las vistas pueden volver a dibujar a sí mismos según sea necesario. El marco de trabajo también solicita al usuario que guarde un archivo modificado antes de cerrarla.

Para implementar los documentos en una aplicación típica, debe hacer lo siguiente:

- Derive una clase de `CDocument` para cada tipo de documento.

- Agregar variables miembro para almacenar los datos de cada documento.

- Implemente las funciones miembro para leer y modificar los datos del documento. Las vistas del documento son los usuarios más importantes de estas funciones de miembro.

- Invalidar el [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) función miembro en la clase de documento para escribir y leer los datos del documento hacia y desde el disco.

`CDocument` admite el envío del documento a través de correo electrónico si no hay soporte técnico de mail (MAPI). Consulte los artículos [MAPI](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

Para obtener más información sobre `CDocument`, consulte [serialización](../../mfc/serialization-in-mfc.md), [temas sobre la arquitectura documento/vista](../../mfc/document-view-architecture.md), y [creación de documento/vista](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="addview"></a>  CDocument::AddView

Llame a esta función para asociar una vista al documento.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Apunta a la vista que se va a agregar.

### <a name="remarks"></a>Comentarios

Esta función agrega la vista especificada a la lista de vistas asociadas con el documento; la función también establece el puntero de documento de la vista en este documento. El marco llama a esta función cuando se asocia un objeto de vista recién creada a un documento. Esto se produce en respuesta a un comando nuevo archivo, abrir archivo o una ventana nueva o cuando se ha dividido una ventana divisora.

Llame a esta función solo si se crean manualmente o asociar una vista. Normalmente, le permitirá que el marco de trabajo conectarse documentos y vistas mediante la definición de un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, la clase de vista y la clase de ventana de marco.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>  CDocument::BeginReadChunks

Inicializa fragmentos de lectura.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Comentarios

##  <a name="cancloseframe"></a>  CDocument::CanCloseFrame

Lo llama el marco de trabajo antes de cerrar una ventana de marco que se muestra el documento.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
Apunta a la ventana de marco de una vista asociada al documento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro cerrar la ventana de marco; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada comprueba si hay otras ventanas de marco que se muestra el documento. Si la ventana de marco especificado es el último que muestra el documento, la función solicita al usuario que guarde el documento si se ha modificado. Reemplace esta función si desea realizar un procesamiento especial cuando se cierra una ventana de marco. Esto es un avanzado que se puede invalidar.

##  <a name="cdocument"></a>  CDocument::CDocument

Construye un objeto `CDocument`.

```
CDocument();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo administra la creación de documento para usted. Invalidar el [OnNewDocument](#onnewdocument) función miembro para realizar la inicialización en una base por documento; esto es especialmente importante en las aplicaciones de único documento (SDI) de la interfaz.

##  <a name="clearchunklist"></a>  CDocument::ClearChunkList

Borra la lista de fragmentos.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Comentarios

##  <a name="clearpathname"></a>  CDocument::ClearPathName

Borra la ruta de acceso del objeto de documento.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Comentarios

Borrar la ruta de acceso de un `CDocument` objeto hace que la aplicación pedir al usuario cuando el documento se guarda a continuación. Esto hace que un **guardar** comando se comportan como un **Guardar como** comando.

##  <a name="deletecontents"></a>  CDocument::DeleteContents

Lo llama el marco de trabajo para eliminar los datos del documento sin destruir el `CDocument` propio objeto.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Comentarios

Se llama justo antes de que el documento está a punto de ser destruida. También se denomina para asegurarse de que un documento está vacío antes de que se vuelve a usar. Esto es especialmente importante para una aplicación SDI, que se usa solo un documento; el documento se reutiliza siempre que el usuario crea o abre otro documento. Llame a esta función para implementar una "Editar borrar todo" o un comando similar que se elimina todos los datos del documento. La implementación predeterminada de esta función no hace nada. Reemplace esta función para eliminar los datos en el documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>  CDocument::FindChunk

Busca un fragmento con un GUID especificado.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parámetros

*guid*<br/>
Especifica el GUID de un fragmento a buscar.

*pid*<br/>
Especifica un PID de un fragmento a buscar.

### <a name="return-value"></a>Valor devuelto

Posición en la lista de fragmentos interno si se realiza correctamente. En caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

##  <a name="getadapter"></a>  CDocument::GetAdapter

Devuelve un puntero a un objeto que implementa el `IDocument` interfaz.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto que implementa el `IDocument` interfaz.

### <a name="remarks"></a>Comentarios

##  <a name="getdoctemplate"></a>  CDocument::GetDocTemplate

Llame a esta función para obtener un puntero a la plantilla de documento para este tipo de documento.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la plantilla de documento para este tipo de documento, o NULL si el documento no está administrado por una plantilla de documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>  CDocument::GetFile

Llame a esta función miembro para obtener un puntero a un `CFile` objeto.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta.

*pError*<br/>
Un puntero a un objeto de excepción de archivo existente que indica el estado de finalización de la operación.

*nOpenFlags*<br/>
Modo de acceso y uso compartido. Especifica la acción que se realizará al abrir el archivo. Puede combinar las opciones que aparecen en el constructor CFile [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) mediante el uso de la operación OR bit a bit (&#124;) operador. Permiso de acceso uno a y un recurso compartido de opción son necesarios; el `modeCreate` y `modeNoInherit` modos son opcionales.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CFile` .

##  <a name="getfirstviewposition"></a>  CDocument::GetFirstViewPosition

Llame a esta función para obtener la posición de la primera vista en la lista de las vistas asociadas al documento.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la iteración con el [GetNextView](#getnextview) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>  CDocument::GetNextView

Llame a esta función para iterar a través de todas las vistas del documento.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*rPosition*<br/>
Devuelve una referencia a un valor de posición mediante una llamada anterior a la `GetNextView` o [GetFirstViewPosition](#getfirstviewposition) funciones miembro. Este valor no debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Un puntero a la vista identificada por *rPosition*.

### <a name="remarks"></a>Comentarios

La función devuelve la vista identificada por *rPosition* y, a continuación, establece *rPosition* en el valor de posición de la vista siguiente en la lista. Si la vista recuperada es el último en la lista, a continuación, *rPosition* se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>  CDocument::GetPathName

Llame a esta función para obtener la ruta de acceso completa del archivo de disco del documento.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta de acceso completa del documento. Esta cadena está vacía si el documento no se ha guardado o no tiene un archivo de disco asociado con él.

##  <a name="getthumbnail"></a>  CDocument::GetThumbnail

Crea un mapa de bits que se usará el proveedor en miniatura para mostrar la miniatura.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parámetros

*cx*<br/>
Especifica el ancho y alto del mapa de bits.

*phbmp*<br/>
Contiene un identificador de un mapa de bits, cuando la función devuelve correctamente.

*pdwAlpha*<br/>
Contiene un DWORD que especifica el valor de canal alfa, cuando la función devuelve correctamente.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si un mapa de bits para la miniatura se creó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="gettitle"></a>  CDocument::GetTitle

Llame a esta función para obtener el título del documento, que normalmente se deriva del nombre de archivo del documento.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Valor devuelto

El título del documento.

##  <a name="initializesearchcontent"></a>  CDocument::InitializeSearchContent

Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para inicializar el contenido de búsqueda. El contenido debe ser una cadena con partes delimitadas por ";". Por ejemplo, "Elija; rectángulo; elemento OLE".

##  <a name="ismodified"></a>  CDocument::IsModified

Llame a esta función para determinar si el documento se ha modificado desde que se guardó por última vez.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se ha modificado desde que se guardó por última vez; en caso contrario, es 0.

##  <a name="issearchandorganizehandler"></a>  CDocument::IsSearchAndOrganizeHandler

Indica si esta instancia de `CDocument` se creó para el controlador de búsqueda & Organizar.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si esta instancia de `CDocument` se creó para el controlador de búsqueda & Organizar.

### <a name="remarks"></a>Comentarios

Actualmente, esta función devuelve TRUE solo para los controladores de vista previa avanzada implementados en un servidor fuera de proceso. Puede establecer las marcas apropiadas (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) en el nivel de aplicación para realizar esta función devuelve TRUE.

##  <a name="loaddocumentfromstream"></a>  CDocument::LoadDocumentFromStream

Se llama para cargar los datos del documento desde una secuencia.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
Un puntero a una secuencia. Esta secuencia proporcionada por el Shell.

*dwGrfMode*<br/>
Modo de acceso a la secuencia.

### <a name="return-value"></a>Valor devuelto

S_OK si la operación de carga se realiza correctamente, en caso contrario HRESULT con un código de error.

### <a name="remarks"></a>Comentarios

Puede invalidar este método en una clase derivada para personalizar cómo cargar datos de la secuencia.

##  <a name="m_bgetthumbnailmode"></a>  CDocument::m_bGetThumbnailMode

Especifica que el `CDocument` objeto fue creado por dllhost para las miniaturas. Debe activarse en `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Comentarios

`TRUE` indica que el documento se creó con dllhost para las miniaturas.

##  <a name="m_bpreviewhandlermode"></a>  CDocument::m_bPreviewHandlerMode

Especifica que el `CDocument` objeto fue creado por prevhost para vista previa avanzada. Debe activarse en `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Comentarios

TRUE indica que el documento se creó con prevhost para vista previa avanzada.

##  <a name="m_bsearchmode"></a>  CDocument::m_bSearchMode

Especifica que el `CDocument` se creó el objeto indizador o por otra aplicación de búsqueda.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Comentarios

`TRUE` indica que el documento se creó mediante el indizador o por otra aplicación de búsqueda.

##  <a name="m_clrrichpreviewbackcolor"></a>  CDocument::m_clrRichPreviewBackColor

Especifica el color de fondo de la ventana de vista previa avanzada. Este color se establece por host.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Comentarios

##  <a name="m_clrrichpreviewtextcolor"></a>  CDocument::m_clrRichPreviewTextColor

Especifica el color de primer plano de la ventana de vista previa avanzada. Este color se establece por host.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Comentarios

##  <a name="m_lfrichpreviewfont"></a>  CDocument::m_lfRichPreviewFont

Especifica la fuente del texto de la ventana de vista previa avanzada. Esta información de fuente se establece por host.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Comentarios

##  <a name="onbeforerichpreviewfontchanged"></a>  CDocument::OnBeforeRichPreviewFontChanged

Se llama antes de cambia la fuente de vista previa avanzada.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Comentarios

##  <a name="onchangedviewlist"></a>  CDocument::OnChangedViewList

Lo llama el marco de trabajo después de una vista se agrega o se quitan del documento.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función comprueba si la última vista se va a quitar y, si es así, elimina el documento. Reemplace esta función si desea realizar un procesamiento especial cuando el marco de trabajo agrega o quita una vista. Por ejemplo, si desea que un documento en cursores siguen abiertos incluso cuando no hay ninguna vista asociada a él, debe reemplazar esta función.

##  <a name="onclosedocument"></a>  CDocument::OnCloseDocument

Lo llama el marco de trabajo cuando se cierra el documento, normalmente como parte del comando Archivo Cerrar.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función destruye todos los marcos que se utiliza para ver el documento, se cierra la vista, limpia el contenido del documento y, a continuación, llama a la [DeleteContents](#deletecontents) función miembro para eliminar el documento datos.

Reemplace esta función si desea realizar el procesamiento de limpieza especial cuando el marco de trabajo cierra un documento. Por ejemplo, si el documento representa un registro en una base de datos, es posible que desee reemplazar esta función para cerrar la base de datos. Debe llamar a la versión de esta función de la clase base desde el reemplazo.

##  <a name="oncreatepreviewframe"></a>  CDocument::OnCreatePreviewFrame

Lo llama el marco de trabajo cuando es necesario crear un fotograma de vista previa para vista previa avanzada.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el marco se ha creado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="ondocumentevent"></a>  CDocument::OnDocumentEvent

Lo llama el marco de trabajo en respuesta a un evento de documento.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parámetros

*deEvent*<br/>
[in] Tipo de datos enumerado que describe el tipo de evento.

### <a name="remarks"></a>Comentarios

Eventos de documentos pueden afectar a varias clases. Este método es responsable de controlar los eventos de documento que afectan a las clases que no sea el [CDocument (clase)](../../mfc/reference/cdocument-class.md). Actualmente, la única clase que debe responder a eventos de documentos es la [CDataRecoveryHandler (clase)](../../mfc/reference/cdatarecoveryhandler-class.md). El `CDocument` clase tiene otros métodos puede invalidarse responsables de controlar el efecto en el `CDocument`.

La tabla siguiente enumeran los valores posibles para *deEvent* y los eventos que corresponden a.

|Valor|Evento correspondiente|
|-----------|-------------------------|
|`onAfterNewDocument`|Se creó un nuevo documento.|
|`onAfterOpenDocument`|Se abre un documento nuevo.|
|`onAfterSaveDocument`|Se guardó el documento.|
|`onAfterCloseDocument`|Se cerró el documento.|

##  <a name="ondrawthumbnail"></a>  CDocument::OnDrawThumbnail

Invalide este método en una clase derivada para dibujar la miniatura.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
Una referencia a un contexto de dispositivo.

*lprcBounds*<br/>
Especifica un rectángulo delimitador del área donde se debe dibujar la miniatura.

### <a name="remarks"></a>Comentarios

##  <a name="onfilesendmail"></a>  CDocument::OnFileSendMail

Envía un mensaje en el host de correo electrónico residente (si existe) con el documento como datos adjuntos.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Comentarios

`OnFileSendMail` las llamadas [OnSaveDocument](#onsavedocument) para serializar (documentos sin título y modificados en un archivo temporal, que, a continuación, se envía por correo electrónico Guardar). Si el documento no se ha modificado, no es necesario un archivo temporal; se envía el original. `OnFileSendMail` carga MAPI32. Archivo DLL si ya no se ha cargado.

Una implementación especial de `OnFileSendMail` para [COleDocument](../../mfc/reference/coledocument-class.md) compuesta de identificadores de archivos correctamente.

`CDocument` admite el envío del documento a través de correo electrónico si no hay soporte técnico de mail (MAPI). Consulte los artículos [MAPI temas](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="onloaddocumentfromstream"></a>  CDocument::OnLoadDocumentFromStream

Lo llama el marco de trabajo cuando es necesario cargar los datos del documento desde una secuencia.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
Un puntero a un flujo de entrada.

*grfMode*<br/>
Modo de acceso a la secuencia.

### <a name="return-value"></a>Valor devuelto

S_OK si la carga se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="onnewdocument"></a>  CDocument::OnNewDocument

Lo llama el marco de trabajo como parte del comando archivo nuevo.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se ha inicializado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función llama a la [DeleteContents](#deletecontents) función miembro para asegurarse de que el documento está vacío y, a continuación, marca el nuevo documento como limpio. Reemplace esta función para inicializar la estructura de datos de un documento nuevo. Debe llamar a la versión de esta función de la clase base desde el reemplazo.

Si el usuario elige el comando nuevo archivo en una aplicación SDI, el marco usa esta función para reinicializar el documento existente, en lugar de crear uno nuevo. Si el usuario elige nuevo archivo en una aplicación de múltiples documentos (MDI) de la interfaz, el marco de trabajo cada vez que crea un nuevo documento y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización de esta función en lugar de en el constructor del comando archivo nuevo ser eficaz en las aplicaciones SDI.

Tenga en cuenta que hay casos donde `OnNewDocument` se llama dos veces. Esto se produce cuando el documento se incrusta como un servidor de documentos de ActiveX. Primero se llama a la función el `CreateInstance` método (expuestos por el `COleObjectFactory`-clase derivada) y una segunda vez mediante la `InitNew` método (expuestos por el `COleServerDoc`-clase derivada).

### <a name="example"></a>Ejemplo

Los ejemplos siguientes muestran métodos alternativos de inicializar un objeto de documento.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>  CDocument::OnOpenDocument

Lo llama el marco de trabajo como parte del comando Abrir archivo.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta a la ruta de acceso del documento que se va a abrir.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se ha cargado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función abre el archivo especificado, llama a la [DeleteContents](#deletecontents) llama la función miembro para asegurarse de que el documento está vacío, [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para leer el archivo contenido y, a continuación, marca el documento como limpio. Reemplace esta función si desea usar algo distinto que el mecanismo de almacenamiento o el archivo. Por ejemplo, podría escribir una aplicación donde documentos representan registros en una base de datos en lugar de en archivos independientes.

Si el usuario elige el comando Abrir archivo en una aplicación SDI, el marco de trabajo usa esta función para reinicializar existente `CDocument` objeto, en lugar de crear uno nuevo. Si el usuario elige abrir archivo en una aplicación MDI, el marco de trabajo construye un nuevo `CDocument` objeto cada vez y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización de esta función en lugar de en el constructor para el comando Abrir archivo para ser eficaz en las aplicaciones SDI.

### <a name="example"></a>Ejemplo

Los ejemplos siguientes muestran métodos alternativos de inicializar un objeto de documento.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>  CDocument::OnPreviewHandlerQueryFocus

Dirige el controlador de vista previa para devolver el HWND recuperados de llamar a la `GetFocus` función.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parámetros

*phwnd*<br/>
[out] Cuando este método finaliza, contiene un puntero al HWND devuelto desde la llamada la `GetFocus` función desde el subproceso en primer plano del controlador de vista previa.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente; o un valor de error en caso contrario.

### <a name="remarks"></a>Comentarios

##  <a name="onpreviewhandlertranslateaccelerator"></a>  CDocument::OnPreviewHandlerTranslateAccelerator

Dirige el controlador de vista previa para controlar una pulsación de tecla Subir de nivel de la bomba de mensaje del proceso en el que se está ejecutando el controlador de vista previa.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parámetros

*pmsg*<br/>
[in] Un puntero a un mensaje de ventana.

### <a name="return-value"></a>Valor devuelto

Si el mensaje de pulsación de tecla puede ser procesado por el controlador de vista previa, el controlador lo procesa y devuelve S_OK. Si el controlador de vista previa no puede procesar el mensaje de pulsación de tecla, ofrece al host a través de `IPreviewHandlerFrame::TranslateAccelerator`. Si el host procesa el mensaje, este método devuelve S_OK. Si el host no procesa el mensaje, este método devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="onrichpreviewbackcolorchanged"></a>  CDocument::OnRichPreviewBackColorChanged

Se llama cuando ha cambiado el color de fondo de vista previa avanzada.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Comentarios

##  <a name="onrichpreviewfontchanged"></a>  CDocument::OnRichPreviewFontChanged

Se llama cuando ha cambiado la fuente de vista previa avanzada.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Comentarios

##  <a name="onrichpreviewsitechanged"></a>  CDocument::OnRichPreviewSiteChanged

Se llama cuando ha cambiado el sitio de vista previa avanzada.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Comentarios

##  <a name="onrichpreviewtextcolorchanged"></a>  CDocument::OnRichPreviewTextColorChanged

Se llama cuando ha cambiado el color del texto de vista previa avanzada.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Comentarios

##  <a name="onsavedocument"></a>  CDocument::OnSaveDocument

Lo llama el marco de trabajo como parte del comando Archivo Guardar o guardar como.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta a la ruta de acceso completa a la que se debe guardar el archivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se guardó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función abre el archivo especificado, llamadas [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para escribir los datos del documento para el archivo y, a continuación, marca el documento como limpiar. Reemplace esta función si desea realizar un procesamiento especial cuando el marco de trabajo guarda un documento. Por ejemplo, podría escribir una aplicación donde documentos representan registros en una base de datos en lugar de en archivos independientes.

##  <a name="onunloadhandler"></a>  CDocument::OnUnloadHandler

Lo llama el marco de trabajo cuando se descarga el controlador de vista previa.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Comentarios

##  <a name="onupdatefilesendmail"></a>  CDocument::OnUpdateFileSendMail

Habilita el comando ID_FILE_SEND_MAIL si no hay soporte técnico de mail (MAPI).

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Un puntero a la [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto asociado con el comando ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Comentarios

En caso contrario, la función quita el comando ID_FILE_SEND_MAIL desde el menú, incluidos los separadores por encima o por debajo del elemento de menú según corresponda. MAPI se habilita si MAPI32. Archivo DLL está presente en la ruta de acceso y, en la sección [correo electrónico] de la VICTORIA. Archivo INI, MAPI = 1. La mayoría de las aplicaciones colocan este comando en el menú archivo.

`CDocument` admite el envío del documento a través de correo electrónico si no hay soporte técnico de mail (MAPI). Consulte los artículos [MAPI temas](../../mfc/mapi.md) y [compatibilidad MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="precloseframe"></a>  CDocument::PreCloseFrame

Esta función miembro se llama el marco de trabajo antes de que se destruye la ventana de marco.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
Puntero a la [CFrameWnd](../../mfc/reference/cframewnd-class.md) que contiene el asociado `CDocument` objeto.

### <a name="remarks"></a>Comentarios

Se puede invalidar para proporcionar la limpieza personalizada, pero no olvide llamar a la clase base también.

El valor predeterminado de `PreCloseFrame` no hace nada `CDocument`. El `CDocument`-las clases derivadas [COleDocument](../../mfc/reference/coledocument-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utilizar esta función miembro.

##  <a name="readnextchunkvalue"></a>  CDocument::ReadNextChunkValue

Lee el siguiente valor de fragmento.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parámetros

*ppValue*<br/>
[out] La función que devuelve *ppValue* contiene el valor que se leyó.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

##  <a name="releasefile"></a>  CDocument::ReleaseFile

Esta función miembro se llama el marco de trabajo para liberar un archivo, que están disponibles para su uso por otras aplicaciones.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Un puntero al objeto CFile para liberarse.

*bAbort*<br/>
Especifica si el archivo es liberarse mediante el uso `CFile::Close` o `CFile::Abort`. FALSE si el archivo es para liberarse mediante [CFile::Close](../../mfc/reference/cfile-class.md#close); TRUE si el archivo se liberarse mediante [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Comentarios

Si *bAbort* es TRUE, `ReleaseFile` llamadas `CFile::Abort`, y se libera el archivo. `CFile::Abort` no se iniciará una excepción.

Si *bAbort* es FALSE, `ReleaseFile` llamadas `CFile::Close` y se libera el archivo.

Reemplace esta función miembro para requerir una acción por parte del usuario antes de publica el archivo.

##  <a name="removechunk"></a>  CDocument::RemoveChunk

Quita un fragmento con el GUID especificado.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parámetros

*Guid*<br/>
Especifica el GUID de un fragmento que se va a quitar.

*Pid*<br/>
Especifica el PID de un fragmento que se va a quitar.

### <a name="remarks"></a>Comentarios

##  <a name="removeview"></a>  CDocument::RemoveView

Llame a esta función para desasociar una vista de un documento.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Apunta a la vista que se va a quitar.

### <a name="remarks"></a>Comentarios

Esta función quita la vista especificada en la lista de vistas asociadas con el documento; puntero al documento de la vista también establece en NULL. Esta función se llama el marco de trabajo cuando se cierra una ventana de marco o se cierra un panel de una ventana divisora.

Llame a esta función sólo si manualmente se desasociar una vista. Normalmente, se permitirá el marco de trabajo separar documentos y vistas mediante la definición de un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, la clase de vista y la clase de ventana de marco.

Vea el ejemplo de [AddView](#addview) para una implementación de ejemplo.

##  <a name="reportsaveloadexception"></a>  CDocument::ReportSaveLoadException

Se llama si se produce una excepción (normalmente un [CFileException](../../mfc/reference/cfileexception-class.md) o [CArchiveException](../../mfc/reference/carchiveexception-class.md)) al guardar o cargar el documento.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Señala al nombre del documento que se va a guardar o cargar.

*e*<br/>
Apunta a la excepción que se produjo. Puede ser NULL.

*bSaving*<br/>
Marca que indica qué operación estaba en curso; distinto de cero si el documento que se guardó, 0 si el documento que se cargó.

*nIDPDefault*<br/>
Identificador del mensaje de error que se mostrará si la función no especifica otra más específica.

### <a name="remarks"></a>Comentarios

La implementación predeterminada examina el objeto de excepción y busca un mensaje de error que describe concretamente la causa. Si no se encuentra un mensaje concreto o si *e* es NULL, el mensaje general especificado por el *nIDPDefault* se usa el parámetro. La función, a continuación, muestra un cuadro de mensaje que contiene el mensaje de error. Reemplace esta función si desea proporcionar mensajes de error personalizados adicionales. Esto es un avanzado que se puede invalidar.

##  <a name="savemodified"></a>  CDocument::SaveModified

Lo llama el marco de trabajo antes de cerrarse un documento modificado.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro continuar y cerrar el documento. 0 si no se debe cerrar el documento.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función muestra un cuadro de mensaje que pregunta al usuario si desea guardar los cambios en el documento, si se han realizado alguna. Reemplace esta función si su programa requiere que se le pide al otro procedimiento. Esto es un avanzado que se puede invalidar.

##  <a name="setchunkvalue"></a>  CDocument::SetChunkValue

Establece un valor de fragmento.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Especifica un valor de fragmento para establecer.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

##  <a name="setmodifiedflag"></a>  CDocument::SetModifiedFlag

Llame a esta función después de realizar ninguna modificación en el documento.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parámetros

*bModified*<br/>
Marca que indica si se ha modificado el documento.

### <a name="remarks"></a>Comentarios

Al llamar a esta función de forma coherente, se asegura de que el marco de trabajo pide al usuario que guarde los cambios antes de cerrar un documento. Normalmente, debe usar el valor predeterminado de TRUE para el *bModified* parámetro. Para marcar un documento más limpio (no modificado), llame a esta función con un valor FALSE.

##  <a name="setpathname"></a>  CDocument::SetPathName

Llame a esta función para especificar la ruta de acceso completa del archivo de disco del documento.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta a la cadena que se usará como la ruta de acceso para el documento.

*bAddToMRU*<br/>
Determina si el nombre de archivo se agrega a la mayoría de la archivos usados recientemente (MRU). Si es TRUE, se agrega el nombre de archivo; Si es FALSE, no se agrega.

### <a name="remarks"></a>Comentarios

Dependiendo del valor de *bAddToMRU* se agrega la ruta de acceso, o no agrega a la lista MRU mantenida por la aplicación. Tenga en cuenta que algunos documentos no están asociados con un archivo de disco. Llame a esta función solo si va a reemplazar la implementación predeterminada para abrir y guardar archivos utilizados por el marco de trabajo.

##  <a name="settitle"></a>  CDocument::SetTitle

Llame a esta función para especificar el título del documento (la cadena que se muestra en la barra de título de una ventana de marco).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
Apunta a la cadena que se usará como el título del documento.

### <a name="remarks"></a>Comentarios

Llamar a esta función actualiza los títulos de todas las ventanas de marco del documento.

##  <a name="updateallviews"></a>  CDocument::UpdateAllViews

Llame a esta función después de que se ha modificado el documento.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parámetros

*pSender*<br/>
Apunta a la vista que se modificó el documento, o NULL si todas las vistas que se van a actualizarse.

*lHint*<br/>
Contiene información sobre la modificación.

*pHint*<br/>
Apunta a un objeto que almacena información sobre la modificación.

### <a name="remarks"></a>Comentarios

Debe llamar a esta función después de llamar a la [SetModifiedFlag](#setmodifiedflag) función miembro. Esta función informa a cada vista asociada al documento, excepto para la vista especificada por *pSender*, que se ha modificado el documento. Se suele llamar a esta función de la clase de vista después de que el usuario ha cambiado el documento a través de una vista.

Esta función llama a la [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) ver la función miembro para cada una de las vistas del documento, excepto el envío, pasando *pHint* y *lHint*. Use estos parámetros para pasar información a las vistas acerca de las modificaciones realizadas en el documento. Puede codificar información mediante *lHint* o puede definir un [CObject](../../mfc/reference/cobject-class.md)-clase derivada para almacenar información sobre las modificaciones y pasar un objeto de esa clase utilizando *pHint*. Invalidar el `CView::OnUpdate` función miembro en su [CView](../../mfc/reference/cview-class.md)-clase derivada para optimizar la actualización de la pantalla de la vista en función de la información pasada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC MDIDOCVW](../../visual-cpp-samples.md)<br/>
[Ejemplo SNAPVW de MFC](../../visual-cpp-samples.md)<br/>
[Ejemplo de MFC NPP](../../visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)
