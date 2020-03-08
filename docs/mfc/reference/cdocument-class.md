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
ms.openlocfilehash: 2d87ff67000fb5b70c0a5c965638875e6f50b22c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856766"
---
# <a name="cdocument-class"></a>CDocument (clase)

Proporciona la funcionalidad básica para las clases definidas por el usuario del documento.

## <a name="syntax"></a>Sintaxis

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocument:: CDocument](#cdocument)|Construye un objeto `CDocument`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocument:: AddView](#addview)|Adjunta una vista al documento.|
|[CDocument:: BeginReadChunks](#beginreadchunks)|Inicializa la lectura de fragmentos.|
|[CDocument:: CanCloseFrame](#cancloseframe)|Overridable avanzado; se llama antes de cerrar una ventana de marco que vea este documento.|
|[CDocument:: ClearChunkList](#clearchunklist)|Borra la lista de fragmentos.|
|[CDocument:: ClearPathName](#clearpathname)|Borra la ruta de acceso del objeto de documento.|
|[CDocument::D eleteContents](#deletecontents)|Se llama para realizar la limpieza del documento.|
|[CDocument:: FindChunk](#findchunk)|Busca un fragmento con el GUID especificado.|
|[CDocument:: GetAdapter](#getadapter)|Devuelve un puntero al objeto que implementa `IDocument` interfaz.|
|[CDocument:: GetDocTemplate](#getdoctemplate)|Devuelve un puntero a la plantilla de documento que describe el tipo del documento.|
|[CDocument:: GetFile](#getfile)|Devuelve un puntero al objeto `CFile` deseado.|
|[CDocument:: GetFirstViewPosition](#getfirstviewposition)|Devuelve la posición de la primera en la lista de vistas; se utiliza para iniciar la iteración.|
|[CDocument:: GetNextView](#getnextview)|Recorre en iteración la lista de vistas asociada al documento.|
|[CDocument:: GetPathName](#getpathname)|Devuelve la ruta de acceso del archivo de datos del documento.|
|[CDocument:: GetThumbnail](#getthumbnail)|Se llama para crear un mapa de bits que va a usar el proveedor de miniaturas para mostrar la miniatura.|
|[CDocument:: GetTitle](#gettitle)|Devuelve el título del documento.|
|[CDocument:: InitializeSearchContent](#initializesearchcontent)|Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.|
|[CDocument:: IsModified](#ismodified)|Indica si el documento se ha modificado desde que se guardó por última vez.|
|[CDocument:: IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indica si esta instancia de `CDocument` objeto se creó para la búsqueda & controlador de la organización.|
|[CDocument:: LoadDocumentFromStream](#loaddocumentfromstream)|Se llama para cargar datos de documento de la secuencia.|
|[CDocument:: OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Se llama antes de cambiar la fuente enriquecida de vista previa.|
|[CDocument:: OnChangedViewList](#onchangedviewlist)|Se llama después de agregar o quitar una vista del documento.|
|[CDocument:: OnCloseDocument](#onclosedocument)|Se llama para cerrar el documento.|
|[CDocument:: OnCreatePreviewFrame](#oncreatepreviewframe)|Lo llama el marco de trabajo cuando necesita crear un marco de vista previa para la vista previa enriquecida.|
|[CDocument:: OnDocumentEvent](#ondocumentevent)|Lo llama el marco de trabajo en respuesta a un evento de documento.|
|[CDocument:: OnDrawThumbnail](#ondrawthumbnail)|Invalide este método en una clase derivada para dibujar el contenido de la miniatura.|
|[CDocument:: OnLoadDocumentFromStream](#onloaddocumentfromstream)|Lo llama el marco de trabajo cuando necesita cargar los datos del documento de la secuencia.|
|[CDocument:: OnNewDocument](#onnewdocument)|Se llama para crear un nuevo documento.|
|[CDocument:: OnOpenDocument](#onopendocument)|Se llama para abrir un documento existente.|
|[CDocument:: OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Dirige el controlador de vista previa para devolver el HWND de la llamada a la función GetFocus.|
|[CDocument:: OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Dirige el controlador de vista previa para controlar una pulsación de tecla pasada desde el bombeo de mensajes del proceso en el que se está ejecutando el controlador de vista previa.|
|[CDocument:: OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Se llama cuando el color de fondo de la vista previa enriquecida ha cambiado.|
|[CDocument:: OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Se llama cuando cambia la fuente de vista previa enriquecida.|
|[CDocument:: OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Se llama cuando el sitio de vista previa enriquecida ha cambiado.|
|[CDocument:: OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Se llama cuando el color del texto de vista previa enriquecida ha cambiado.|
|[CDocument:: OnSaveDocument](#onsavedocument)|Se llama para guardar el documento en el disco.|
|[CDocument:: OnUnloadHandler](#onunloadhandler)|Lo llama el marco de trabajo cuando se está descargando el controlador de vista previa.|
|[CDocument::P reCloseFrame](#precloseframe)|Se llama antes de cerrar la ventana de marco.|
|[CDocument:: ReadNextChunkValue](#readnextchunkvalue)|Lee el valor del fragmento siguiente.|
|[CDocument:: ReleaseFile](#releasefile)|Libera un archivo para que esté disponible para que lo usen otras aplicaciones.|
|[CDocument:: RemoveChunk](#removechunk)|Quita un fragmento con el GUID especificado.|
|[CDocument:: RemoveView](#removeview)|Desasocia una vista del documento.|
|[CDocument:: ReportSaveLoadException](#reportsaveloadexception)|Overridable avanzado; se llama cuando no se puede completar una operación de abrir o guardar debido a una excepción.|
|[CDocument:: SaveModified](#savemodified)|Overridable avanzado; se llama para preguntar al usuario si se debe guardar el documento.|
|[CDocument:: SetChunkValue](#setchunkvalue)|Establece un valor de fragmento.|
|[CDocument:: SetModifiedFlag](#setmodifiedflag)|Establece una marca que indica que se ha modificado el documento desde que se guardó por última vez.|
|[CDocument:: SetPathName](#setpathname)|Establece la ruta de acceso del archivo de datos utilizado por el documento.|
|[CDocument:: SetTitle](#settitle)|Establece el título del documento.|
|[CDocument:: UpdateAllViews](#updateallviews)|Notifica a todas las vistas que se ha modificado el documento.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDocument:: OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo electrónico con el documento adjunto.|
|[CDocument:: OnUpdateFileSendMail](#onupdatefilesendmail)|Habilita el comando enviar correo si la compatibilidad con correo electrónico está presente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocument:: m_bGetThumbnailMode](#m_bgetthumbnailmode)|Especifica que Dllhost ha creado `CDocument` objeto para las miniaturas. Se debe proteger `CView::OnDraw`.|
|[CDocument:: m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Especifica que prevhost ha creado `CDocument` objeto para `Rich Preview`. Se debe proteger `CView::OnDraw`.|
|[CDocument:: m_bSearchMode](#m_bsearchmode)|Especifica que `CDocument` objeto fue creado por el indizador u otra aplicación de búsqueda.|
|[CDocument:: m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Especifica el color de fondo de la ventana de vista previa enriquecida. Este color lo establece el host.|
|[CDocument:: m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Especifica el color de primer plano de la ventana de vista previa enriquecida. Este color lo establece el host.|
|[CDocument:: m_lfRichPreviewFont](#m_lfrichpreviewfont)|Especifica la fuente de texto para la ventana de vista previa enriquecida. Esta información de fuente se establece mediante el host.|

## <a name="remarks"></a>Observaciones

Un documento representa la unidad de datos que el usuario suele abrir con el comando archivo abrir y lo guarda con el comando Guardar archivo.

`CDocument` admite operaciones estándar como la creación de un documento, su carga y su guardado. El marco de trabajo manipula los documentos mediante la interfaz definida por `CDocument`.

Una aplicación puede admitir más de un tipo de documento; por ejemplo, una aplicación puede admitir las hojas de cálculo y los documentos de texto. Cada tipo de documento tiene una plantilla de documento asociada; la plantilla de documento especifica qué recursos (por ejemplo, el menú, el icono o la tabla de aceleradores) se usan para ese tipo de documento. Cada documento contiene un puntero a su objeto `CDocTemplate` asociado.

Los usuarios interactúan con un documento a través de los objetos de [CView](../../mfc/reference/cview-class.md) asociados a él. Una vista representa una imagen del documento en una ventana de marco e interpreta la entrada del usuario como operaciones en el documento. Un documento puede tener varias vistas asociadas. Cuando el usuario abre una ventana en un documento, el marco de trabajo crea una vista y la adjunta al documento. La plantilla de documento especifica el tipo de vista y la ventana de marco que se usan para mostrar cada tipo de documento.

Los documentos forman parte del enrutamiento de comandos estándar del marco y, por consiguiente, reciben comandos de componentes estándar de la interfaz de usuario (como el elemento de menú guardar archivo). Un documento recibe comandos reenviados por la vista activa. Si el documento no controla un comando determinado, lo reenvía a la plantilla de documento que lo administra.

Cuando se modifican los datos de un documento, cada una de sus vistas debe reflejar esas modificaciones. `CDocument` proporciona la función miembro [UpdateAllViews](#updateallviews) para notificar a las vistas de tales cambios, de modo que las vistas se pueden volver a dibujar según sea necesario. El marco de trabajo también solicita al usuario que guarde un archivo modificado antes de cerrarlo.

Para implementar documentos en una aplicación típica, debe hacer lo siguiente:

- Derive una clase de `CDocument` para cada tipo de documento.

- Agregue variables de miembro para almacenar los datos de cada documento.

- Implemente funciones miembro para leer y modificar los datos del documento. Las vistas del documento son los usuarios más importantes de estas funciones miembro.

- Invalide la función miembro [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) en la clase de documento para escribir y leer los datos del documento en el disco.

`CDocument` admite el envío de un documento a través de mail, si la compatibilidad con correo (MAPI) está presente. Vea los artículos compatibilidad con [MAPI](../../mfc/mapi.md) y [MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

Para obtener más información sobre `CDocument`, vea los temas sobre la [serialización](../../mfc/serialization-in-mfc.md), la [arquitectura de documentos y vistas](../../mfc/document-view-architecture.md), y la [creación de documentos y vistas](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="addview"></a>CDocument:: AddView

Llame a esta función para adjuntar una vista al documento.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Apunta a la vista que se va a agregar.

### <a name="remarks"></a>Observaciones

Esta función agrega la vista especificada a la lista de vistas asociada al documento; la función también establece el puntero de documento de la vista en este documento. El marco de trabajo llama a esta función cuando se adjunta un objeto de vista recién creado a un documento; Esto sucede en respuesta a un archivo nuevo, abrir archivo o nuevo comando de la ventana o cuando se divide una ventana divisora.

Llame a esta función solo si va a crear y adjuntar una vista manualmente. Normalmente, permitirá que el marco Conecte documentos y vistas definiendo un objeto [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) para asociar una clase de documento, una clase de vista y una clase de ventana de marco.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>CDocument:: BeginReadChunks

Inicializa la lectura de fragmentos.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Observaciones

##  <a name="cancloseframe"></a>CDocument:: CanCloseFrame

Lo llama el marco de trabajo antes de que se cierre una ventana de marco que muestre el documento.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
Apunta a la ventana de marco de una vista adjunta al documento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro cerrar la ventana de marco; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada comprueba si hay otras ventanas de marco que muestren el documento. Si la ventana de marco especificada es la última que muestra el documento, la función solicita al usuario que guarde el documento si se ha modificado. Invalide esta función si desea realizar un procesamiento especial cuando se cierre una ventana de marco. Se trata de un reemplazable avanzado.

##  <a name="cdocument"></a>CDocument:: CDocument

Construye un objeto `CDocument`.

```
CDocument();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo administra la creación del documento. Invalide la función miembro [OnNewDocument](#onnewdocument) para realizar la inicialización por documento; Esto es especialmente importante en las aplicaciones de interfaz de un único documento (SDI).

##  <a name="clearchunklist"></a>CDocument:: ClearChunkList

Borra la lista de fragmentos.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Observaciones

##  <a name="clearpathname"></a>CDocument:: ClearPathName

Borra la ruta de acceso del objeto de documento.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Observaciones

La eliminación de la ruta de acceso de un objeto `CDocument` hace que la aplicación solicite al usuario la próxima vez que se guarde el documento. Esto hace que un comando **Guardar** se comporte como un comando **Guardar como** .

##  <a name="deletecontents"></a>CDocument::D eleteContents

Lo llama el marco de trabajo para eliminar los datos del documento sin destruir el propio objeto de `CDocument`.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Observaciones

Se llama justo antes de que se destruya el documento. También se llama para asegurarse de que un documento está vacío antes de que se reutilice. Esto es especialmente importante para una aplicación SDI, que solo usa un documento; el documento se reutiliza siempre que el usuario crea o abre otro documento. Llame a esta función para implementar un comando "Editar Borrar todo" o similar que elimine todos los datos del documento. La implementación predeterminada de esta función no hace nada. Invalide esta función para eliminar los datos del documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>CDocument:: FindChunk

Busca un fragmento con un GUID especificado.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parámetros

*guid*<br/>
Especifica el GUID de un fragmento que se va a buscar.

*pid*<br/>
Especifica el PID de un fragmento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Posición en la lista de fragmentos interna si se realiza correctamente. De lo contrario, NULL.

### <a name="remarks"></a>Observaciones

##  <a name="getadapter"></a>CDocument:: GetAdapter

Devuelve un puntero a un objeto que implementa la interfaz `IDocument`.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto que implementa la interfaz `IDocument`.

### <a name="remarks"></a>Observaciones

##  <a name="getdoctemplate"></a>CDocument:: GetDocTemplate

Llame a esta función para obtener un puntero a la plantilla de documento para este tipo de documento.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la plantilla de documento para este tipo de documento, o NULL si el documento no está administrado por una plantilla de documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>CDocument:: GetFile

Llame a esta función miembro para obtener un puntero a un objeto `CFile`.

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
Uso compartido y modo de acceso. Especifica la acción que se realizará al abrir el archivo. Puede combinar las opciones que se muestran en el constructor CFile CFile [:: CFile](../../mfc/reference/cfile-class.md#cfile) mediante el operador bit&#124;a bit or (). Se requieren un permiso de acceso y una opción de recurso compartido; los modos `modeCreate` y `modeNoInherit` son opcionales.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CFile` .

##  <a name="getfirstviewposition"></a>CDocument:: GetFirstViewPosition

Llame a esta función para obtener la posición de la primera vista en la lista de vistas asociada al documento.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de posición que se puede usar para la iteración con la función miembro [GetNextView](#getnextview) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>CDocument:: GetNextView

Llame a esta función para recorrer en iteración todas las vistas del documento.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*rPosition*<br/>
Referencia a un valor de posición devuelto por una llamada anterior a las funciones miembro `GetNextView` o [GetFirstViewPosition](#getfirstviewposition) . Este valor no debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Un puntero a la vista identificada por *rPosition*.

### <a name="remarks"></a>Observaciones

La función devuelve la vista identificada por *rPosition* y, a continuación, establece *rPosition* en el valor de posición de la vista siguiente en la lista. Si la vista recuperada es la última de la lista, *rPosition* se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>CDocument:: GetPathName

Llame a esta función para obtener la ruta de acceso completa del archivo de disco del documento.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa del documento. Esta cadena está vacía si el documento no se ha guardado o no tiene asociado un archivo de disco.

##  <a name="getthumbnail"></a>CDocument:: GetThumbnail

Crea un mapa de bits que usará el proveedor de miniaturas para mostrar la miniatura.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parámetros

*serie*<br/>
Especifica el ancho y el alto del mapa de bits.

*phbmp*<br/>
Contiene un identificador de un mapa de bits, cuando la función se devuelve correctamente.

*pdwAlpha*<br/>
Contiene un valor DWORD que especifica el valor del canal alfa cuando la función se devuelve correctamente.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha creado correctamente un mapa de bits para la miniatura; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

##  <a name="gettitle"></a>CDocument:: GetTitle

Llame a esta función para obtener el título del documento, que normalmente se deriva del nombre de archivo del documento.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Valor devuelto

Título del documento.

##  <a name="initializesearchcontent"></a>CDocument:: InitializeSearchContent

Se llama para inicializar el contenido de búsqueda del controlador de búsqueda.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para inicializar el contenido de la búsqueda. El contenido debe ser una cadena con partes delimitadas por ";". Por ejemplo, "Point; rectángulo elemento OLE ".

##  <a name="ismodified"></a>CDocument:: IsModified

Llame a esta función para determinar si el documento se ha modificado desde que se guardó por última vez.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se ha modificado desde que se guardó por última vez; de lo contrario, es 0.

##  <a name="issearchandorganizehandler"></a>CDocument:: IsSearchAndOrganizeHandler

Indica si esta instancia de `CDocument` se creó para el controlador de búsqueda & organizar.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si esta instancia de `CDocument` se creó para el controlador de la búsqueda & organizar.

### <a name="remarks"></a>Observaciones

Actualmente, esta función devuelve TRUE solo para los controladores de vista previa enriquecidos implementados en un servidor fuera de proceso. Puede establecer las marcas adecuadas (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) en el nivel de aplicación para que esta función devuelva TRUE.

##  <a name="loaddocumentfromstream"></a>CDocument:: LoadDocumentFromStream

Se llama para cargar datos de documento de una secuencia.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
Un puntero a un flujo. El Shell proporciona esta secuencia.

*dwGrfMode*<br/>
Modo de acceso a la secuencia.

### <a name="return-value"></a>Valor devuelto

S_OK si la operación de carga se realiza correctamente; de lo contrario, HRESULT con un código de error.

### <a name="remarks"></a>Observaciones

Puede invalidar este método en una clase derivada para personalizar cómo se cargan los datos de la secuencia.

##  <a name="m_bgetthumbnailmode"></a>CDocument:: m_bGetThumbnailMode

Especifica que Dllhost ha creado el objeto `CDocument` para las miniaturas. Se debe proteger `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Observaciones

`TRUE` indica que Dllhost creó el documento para las miniaturas.

##  <a name="m_bpreviewhandlermode"></a>CDocument:: m_bPreviewHandlerMode

Especifica que prevhost ha creado el objeto de `CDocument` para obtener una vista previa enriquecida. Se debe proteger `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Observaciones

TRUE indica que el documento fue creado por prevhost para la vista previa enriquecida.

##  <a name="m_bsearchmode"></a>CDocument:: m_bSearchMode

Especifica que el `CDocument` objeto fue creado por el indizador o por otra aplicación de búsqueda.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Observaciones

`TRUE` indica que el documento fue creado por el indexador o por otra aplicación de búsqueda.

##  <a name="m_clrrichpreviewbackcolor"></a>CDocument:: m_clrRichPreviewBackColor

Especifica el color de fondo de la ventana de vista previa enriquecida. Este color lo establece el host.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Observaciones

##  <a name="m_clrrichpreviewtextcolor"></a>CDocument:: m_clrRichPreviewTextColor

Especifica el color de primer plano de la ventana de vista previa enriquecida. Este color lo establece el host.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Observaciones

##  <a name="m_lfrichpreviewfont"></a>CDocument:: m_lfRichPreviewFont

Especifica la fuente de texto de la ventana de vista previa enriquecida. Esta información de fuente se establece mediante el host.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Observaciones

##  <a name="onbeforerichpreviewfontchanged"></a>CDocument:: OnBeforeRichPreviewFontChanged

Se llama antes de cambiar la fuente enriquecida de vista previa.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Observaciones

##  <a name="onchangedviewlist"></a>CDocument:: OnChangedViewList

Lo llama el marco de trabajo después de agregar o quitar una vista del documento.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función comprueba si se está quitando la última vista y, en caso afirmativo, elimina el documento. Invalide esta función si desea realizar un procesamiento especial cuando el marco de trabajo agrega o quita una vista. Por ejemplo, si desea que un documento permanezca abierto aunque no haya ninguna vista adjunta, invalide esta función.

##  <a name="onclosedocument"></a>CDocument:: OnCloseDocument

Lo llama el marco de trabajo cuando el documento está cerrado, normalmente como parte del comando de cierre de archivo.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función destruye todos los marcos usados para ver el documento, cierra la vista, limpia el contenido del documento y, a continuación, llama a la función miembro [DeleteContents](#deletecontents) para eliminar los datos del documento.

Invalide esta función si desea realizar un procesamiento de limpieza especial cuando el marco de trabajo cierre un documento. Por ejemplo, si el documento representa un registro en una base de datos, puede que desee invalidar esta función para cerrar la base de datos. Debe llamar a la versión de la clase base de esta función desde la invalidación.

##  <a name="oncreatepreviewframe"></a>CDocument:: OnCreatePreviewFrame

Lo llama el marco de trabajo cuando necesita crear un marco de vista previa para la vista previa enriquecida.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el marco se crea correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

##  <a name="ondocumentevent"></a>CDocument:: OnDocumentEvent

Lo llama el marco de trabajo en respuesta a un evento de documento.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parámetros

*desigual*<br/>
de Un tipo de datos enumerado que describe el tipo de evento.

### <a name="remarks"></a>Observaciones

Los eventos de documento pueden afectar a varias clases. Este método es responsable de controlar los eventos de documento que afectan a clases distintas de la [clase CDocument](../../mfc/reference/cdocument-class.md). Actualmente, la única clase que debe responder a los eventos de documento es la [clase CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). La clase `CDocument` tiene otros métodos reemplazables responsables de controlar el efecto en el `CDocument`.

En la tabla siguiente se enumeran los posibles *valores de los eventos y de los* eventos a los que corresponden.

|Value|Evento correspondiente|
|-----------|-------------------------|
|`onAfterNewDocument`|Se creó un nuevo documento.|
|`onAfterOpenDocument`|Se abrió un nuevo documento.|
|`onAfterSaveDocument`|El documento se ha guardado.|
|`onAfterCloseDocument`|El documento se cerró.|

##  <a name="ondrawthumbnail"></a>CDocument:: OnDrawThumbnail

Invalide este método en una clase derivada para dibujar la miniatura.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
Referencia a un contexto de dispositivo.

*lprcBounds*<br/>
Especifica un rectángulo delimitador del área donde se debe dibujar la miniatura.

### <a name="remarks"></a>Observaciones

##  <a name="onfilesendmail"></a>CDocument:: OnFileSendMail

Envía un mensaje a través del host de correo residente (si existe) con el documento como datos adjuntos.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Observaciones

`OnFileSendMail` llama a [OnSaveDocument](#onsavedocument) para serializar (guardar) documentos sin título y modificados en un archivo temporal, que se envía a través del correo electrónico. Si el documento no se ha modificado, no es necesario un archivo temporal. se envía el original. `OnFileSendMail` carga MAPI32. DLL si aún no se ha cargado.

Una implementación especial de `OnFileSendMail` para [COleDocument](../../mfc/reference/coledocument-class.md) controla correctamente los archivos compuestos.

`CDocument` admite el envío de un documento a través de mail, si la compatibilidad con correo (MAPI) está presente. Vea los artículos [temas de MAPI](../../mfc/mapi.md) y [compatibilidad con MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="onloaddocumentfromstream"></a>CDocument:: OnLoadDocumentFromStream

Lo llama el marco de trabajo cuando necesita cargar los datos del documento desde una secuencia.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
Un puntero a un flujo entrante.

*grfMode*<br/>
Modo de acceso a la secuencia.

### <a name="return-value"></a>Valor devuelto

S_OK si la carga se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Observaciones

##  <a name="onnewdocument"></a>CDocument:: OnNewDocument

Lo llama el marco de trabajo como parte del comando archivo nuevo.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se inicializó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a la función miembro [DeleteContents](#deletecontents) para asegurarse de que el documento está vacío y, a continuación, marca el nuevo documento como Clean. Invalide esta función para inicializar la estructura de datos de un nuevo documento. Debe llamar a la versión de la clase base de esta función desde la invalidación.

Si el usuario elige el comando archivo nuevo en una aplicación SDI, el marco de trabajo usa esta función para reinicializar el documento existente, en lugar de crear uno nuevo. Si el usuario elige archivo nuevo en una aplicación de interfaz de múltiples documentos (MDI), el marco de trabajo crea un nuevo documento cada vez y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización en esta función en lugar de en el constructor para que el comando archivo nuevo surta efecto en las aplicaciones SDI.

Tenga en cuenta que hay casos en los que se llama dos veces a `OnNewDocument`. Esto sucede cuando el documento se incrusta como un servidor de documentos ActiveX. El método `CreateInstance` (expuesto por la clase derivada de `COleObjectFactory`) llama a la función por primera vez y la segunda vez por el método `InitNew` (expuesto por la clase derivada de `COleServerDoc`).

### <a name="example"></a>Ejemplo

En los siguientes ejemplos se muestran métodos alternativos para inicializar un objeto de documento.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>CDocument:: OnOpenDocument

Lo llama el marco de trabajo como parte del comando Abrir archivo.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta a la ruta de acceso del documento que se va a abrir.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se ha cargado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función abre el archivo especificado, llama a la función miembro [DeleteContents](#deletecontents) para asegurarse de que el documento está vacío, llama a [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para leer el contenido del archivo y, a continuación, marca el documento como Clean. Invalide esta función si desea usar algo distinto del mecanismo de archivo o el mecanismo de archivos. Por ejemplo, puede escribir una aplicación en la que los documentos representen registros en una base de datos en lugar de archivos independientes.

Si el usuario elige el comando archivo abrir en una aplicación SDI, el marco de trabajo usa esta función para reinicializar el objeto de `CDocument` existente, en lugar de crear uno nuevo. Si el usuario elige archivo abierto en una aplicación MDI, el marco de trabajo crea un nuevo objeto `CDocument` cada vez y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización en esta función en lugar de en el constructor para que el comando archivo abierto surta efecto en las aplicaciones SDI.

### <a name="example"></a>Ejemplo

En los siguientes ejemplos se muestran métodos alternativos para inicializar un objeto de documento.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>CDocument:: OnPreviewHandlerQueryFocus

Dirige el controlador de vista previa para devolver el HWND recuperado de la llamada a la función `GetFocus`.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parámetros

*phwnd*<br/>
enuncia El resultado que devuelve este método contiene un puntero al HWND devuelto por la llamada a la función `GetFocus` desde el subproceso en primer plano del controlador de vista previa.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente; o un valor de error en caso contrario.

### <a name="remarks"></a>Observaciones

##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument:: OnPreviewHandlerTranslateAccelerator

Dirige el controlador de vista previa para controlar una pulsación de tecla pasada desde el bombeo de mensajes del proceso en el que se está ejecutando el controlador de vista previa.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parámetros

*pmsg*<br/>
de Un puntero a un mensaje de ventana.

### <a name="return-value"></a>Valor devuelto

Si el controlador de vista previa puede procesar el mensaje de pulsación de tecla, el controlador lo procesa y Devuelve S_OK. Si el controlador de vista previa no puede procesar el mensaje de pulsación de tecla, lo ofrece al host a través de `IPreviewHandlerFrame::TranslateAccelerator`. Si el host procesa el mensaje, este método devuelve S_OK. Si el host no procesa el mensaje, este método devuelve S_FALSE.

### <a name="remarks"></a>Observaciones

##  <a name="onrichpreviewbackcolorchanged"></a>CDocument:: OnRichPreviewBackColorChanged

Se llama cuando el color de fondo de la vista previa enriquecida ha cambiado.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Observaciones

##  <a name="onrichpreviewfontchanged"></a>CDocument:: OnRichPreviewFontChanged

Se le llama cuando cambia la fuente de vista previa enriquecida.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Observaciones

##  <a name="onrichpreviewsitechanged"></a>CDocument:: OnRichPreviewSiteChanged

Se llama cuando el sitio de vista previa enriquecida ha cambiado.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Observaciones

##  <a name="onrichpreviewtextcolorchanged"></a>CDocument:: OnRichPreviewTextColorChanged

Se llama cuando el color del texto de la vista previa enriquecida ha cambiado.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Observaciones

##  <a name="onsavedocument"></a>CDocument:: OnSaveDocument

Lo llama el marco de trabajo como parte del comando Guardar archivo o guardar archivo como.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta a la ruta de acceso completa en la que se debe guardar el archivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se ha guardado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función abre el archivo especificado, llama a [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para escribir los datos del documento en el archivo y, a continuación, marca el documento como limpio. Invalide esta función si desea realizar un procesamiento especial cuando el marco de trabajo guarde un documento. Por ejemplo, puede escribir una aplicación en la que los documentos representen registros en una base de datos en lugar de archivos independientes.

##  <a name="onunloadhandler"></a>CDocument:: OnUnloadHandler

Lo llama el marco de trabajo cuando se descarga el controlador de vista previa.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Observaciones

##  <a name="onupdatefilesendmail"></a>CDocument:: OnUpdateFileSendMail

Habilita el comando ID_FILE_SEND_MAIL si la compatibilidad con correo (MAPI) está presente.

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero al objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) asociado al comando ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Observaciones

En caso contrario, la función quita el comando ID_FILE_SEND_MAIL del menú, incluidos los separadores por encima o por debajo del elemento de menú, según corresponda. MAPI está habilitado si MAPI32. DLL está presente en la ruta de acceso y, en la sección [mail] del archivo WIN. Archivo INI, MAPI = 1. La mayoría de las aplicaciones colocan este comando en el menú archivo.

`CDocument` admite el envío de un documento a través de mail, si la compatibilidad con correo (MAPI) está presente. Vea los artículos [temas de MAPI](../../mfc/mapi.md) y [compatibilidad con MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="precloseframe"></a>CDocument::P reCloseFrame

El marco de trabajo llama a esta función miembro antes de que se destruya la ventana de marco.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
Puntero a [CFrameWnd](../../mfc/reference/cframewnd-class.md) que contiene el objeto de `CDocument` asociado.

### <a name="remarks"></a>Observaciones

Se puede invalidar para proporcionar limpieza personalizada, pero asegúrese de llamar también a la clase base.

El valor predeterminado de `PreCloseFrame` no hace nada en `CDocument`. Las clases derivadas de `CDocument`[COleDocument](../../mfc/reference/coledocument-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utilizan esta función miembro.

##  <a name="readnextchunkvalue"></a>CDocument:: ReadNextChunkValue

Lee el siguiente valor de fragmento.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parámetros

*ppValue*<br/>
enuncia Cuando la función devuelve, *ppValue* contiene el valor que se leyó.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

##  <a name="releasefile"></a>CDocument:: ReleaseFile

El marco de trabajo llama a esta función miembro para liberar un archivo, de modo que esté disponible para que lo usen otras aplicaciones.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Puntero al objeto CFile que se va a liberar.

*bAbort*<br/>
Especifica si el archivo se va a liberar mediante `CFile::Close` o `CFile::Abort`. FALSE si el archivo se va a liberar mediante [CFile:: Close](../../mfc/reference/cfile-class.md#close); TRUE si el archivo se va a liberar mediante [CFile:: ABORT](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Observaciones

Si *bAbort* es TRUE, `ReleaseFile` llama a `CFile::Abort`y se libera el archivo. `CFile::Abort` no producirá una excepción.

Si *bAbort* es FALSE, `ReleaseFile` llama a `CFile::Close` y se libera el archivo.

Invalide esta función miembro para requerir una acción por parte del usuario antes de liberar el archivo.

##  <a name="removechunk"></a>CDocument:: RemoveChunk

Quita un fragmento con el GUID especificado.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parámetros

*GUID*<br/>
Especifica el GUID de un fragmento que se va a quitar.

*ID*<br/>
Especifica el PID de un fragmento que se va a quitar.

### <a name="remarks"></a>Observaciones

##  <a name="removeview"></a>CDocument:: RemoveView

Llame a esta función para desasociar una vista de un documento.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Apunta a la vista que se va a quitar.

### <a name="remarks"></a>Observaciones

Esta función quita la vista especificada de la lista de vistas asociada al documento; también establece el puntero de documento de la vista en NULL. El marco de trabajo llama a esta función cuando se cierra una ventana de marco o se cierra un panel de una ventana divisora.

Llame a esta función solo si está desasociando manualmente una vista. Normalmente, el marco de trabajo desasocia documentos y vistas mediante la definición de un objeto [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) para asociar una clase de documento, una clase de vista y una clase de ventana de marco.

Vea el ejemplo en [AddView](#addview) para obtener una implementación de ejemplo.

##  <a name="reportsaveloadexception"></a>CDocument:: ReportSaveLoadException

Se llama si se produce una excepción (normalmente un [CFileException](../../mfc/reference/cfileexception-class.md) o [CArchiveException](../../mfc/reference/carchiveexception-class.md)) mientras se guarda o carga el documento.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta al nombre del documento que se estaba guardando o cargando.

*e*<br/>
Apunta a la excepción que se produjo. Puede ser NULL.

*bSaving*<br/>
Marca que indica qué operación estaba en curso; distinto de cero si se está guardando el documento, 0 si se estaba cargando el documento.

*nIDPDefault*<br/>
Identificador del mensaje de error que se va a mostrar si la función no especifica una más específica.

### <a name="remarks"></a>Observaciones

La implementación predeterminada examina el objeto de excepción y busca un mensaje de error que describe específicamente la causa. Si no se encuentra un mensaje específico o si *e* es null, se utiliza el mensaje general especificado por el parámetro *nIDPDefault* . A continuación, la función muestra un cuadro de mensaje que contiene el mensaje de error. Invalide esta función si desea proporcionar mensajes de error personalizados adicionales. Se trata de un reemplazable avanzado.

##  <a name="savemodified"></a>CDocument:: SaveModified

Lo llama el marco de trabajo antes de que se cierre un documento modificado.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro continuar y cerrar el documento; 0 si no se debe cerrar el documento.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función muestra un cuadro de mensaje que pregunta al usuario si desea guardar los cambios en el documento, en caso de que se haya realizado alguno. Invalide esta función si el programa requiere un procedimiento de solicitud diferente. Se trata de un reemplazable avanzado.

##  <a name="setchunkvalue"></a>CDocument:: SetChunkValue

Establece un valor de fragmento.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Especifica un valor de fragmento que se va a establecer.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

##  <a name="setmodifiedflag"></a>CDocument:: SetModifiedFlag

Llame a esta función después de haber realizado modificaciones en el documento.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parámetros

*bModified*<br/>
Marca que indica si el documento se ha modificado.

### <a name="remarks"></a>Observaciones

Al llamar a esta función de forma coherente, se asegura de que el marco de trabajo solicite al usuario que guarde los cambios antes de cerrar un documento. Normalmente, debe usar el valor predeterminado TRUE para el parámetro *bModified* . Para marcar un documento como limpio (sin modificar), llame a esta función con un valor de FALSE.

##  <a name="setpathname"></a>CDocument:: SetPathName

Llame a esta función para especificar la ruta de acceso completa del archivo de disco del documento.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta a la cadena que se va a utilizar como ruta de acceso del documento.

*bAddToMRU*<br/>
Determina si el nombre de archivo se agrega a la lista de archivos usados más recientemente (MRU). Si es TRUE, se agrega el nombre de archivo; Si es FALSE, no se agrega.

### <a name="remarks"></a>Observaciones

Dependiendo del valor de *bAddToMRU* , la ruta de acceso se agrega, o no se agrega, a la lista MRU mantenida por la aplicación. Tenga en cuenta que algunos documentos no están asociados a un archivo de disco. Llame a esta función solo si va a reemplazar la implementación predeterminada para abrir y guardar archivos usados por el marco de trabajo.

##  <a name="settitle"></a>CDocument:: SetTitle

Llame a esta función para especificar el título del documento (la cadena mostrada en la barra de título de una ventana de marco).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
Apunta a la cadena que se va a utilizar como título del documento.

### <a name="remarks"></a>Observaciones

Al llamar a esta función, se actualizan los títulos de todas las ventanas de marco que muestran el documento.

##  <a name="updateallviews"></a>CDocument:: UpdateAllViews

Llame a esta función una vez que se haya modificado el documento.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parámetros

*pSender*<br/>
Apunta a la vista que modificó el documento, o NULL si se van a actualizar todas las vistas.

*lHint*<br/>
Contiene información sobre la modificación.

*pHint*<br/>
Apunta a un objeto que almacena información sobre la modificación.

### <a name="remarks"></a>Observaciones

Debe llamar a esta función después de llamar a la función miembro [SetModifiedFlag](#setmodifiedflag) . Esta función informa a cada vista adjunta al documento, excepto para la vista especificada por *pSender*, que el documento se ha modificado. Normalmente, se llama a esta función desde la clase de vista una vez que el usuario ha cambiado el documento a través de una vista.

Esta función llama a la función miembro [CView:: ALUpdate](../../mfc/reference/cview-class.md#onupdate) para cada una de las vistas del documento excepto la vista de envío, pasando *pHint* y *lHint*. Utilice estos parámetros para pasar información a las vistas sobre las modificaciones realizadas en el documento. Puede codificar información mediante *lHint* o puede definir una clase derivada de [CObject](../../mfc/reference/cobject-class.md)para almacenar información sobre las modificaciones y pasar un objeto de esa clase mediante *pHint*. Reemplace la función miembro `CView::OnUpdate` en la clase derivada de [CView](../../mfc/reference/cview-class.md)para optimizar la actualización de la presentación de la vista basándose en la información que se ha pasado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)
