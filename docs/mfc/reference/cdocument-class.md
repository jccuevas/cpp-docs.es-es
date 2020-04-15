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
ms.openlocfilehash: 2f8ba8d0b35bd72efa8f8d63dbefd689e645d768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374046"
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
|[CDocument::AddView](#addview)|Adjunta una vista al documento.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicializa la lectura de fragmentos.|
|[CDocument::CanCloseFrame](#cancloseframe)|Avanzado reemplazable; antes de cerrar una ventana de marco que ve este documento.|
|[CDocument::ClearChunkList](#clearchunklist)|Borra la lista de fragmentos.|
|[CDocument::ClearPathName](#clearpathname)|Borra la ruta de acceso del objeto de documento.|
|[CDocument::DeleteContents](#deletecontents)|Se llama para realizar la limpieza del documento.|
|[CDocument::FindChunk](#findchunk)|Busca un fragmento con GUID especificado.|
|[CDocument::GetAdapter](#getadapter)|Devuelve un puntero `IDocument` a la interfaz de implementación de objetos.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Devuelve un puntero a la plantilla de documento que describe el tipo del documento.|
|[CDocument::GetFile](#getfile)|Devuelve un puntero `CFile` al objeto deseado.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Devuelve la posición del primero en la lista de vistas; utilizado para comenzar la iteración.|
|[CDocument::GetNextView](#getnextview)|Recorre en iteración la lista de vistas asociadas al documento.|
|[CDocument::GetPathName](#getpathname)|Devuelve la ruta de acceso del archivo de datos del documento.|
|[CDocument::GetThumbnail](#getthumbnail)|Se llama para crear un mapa de bits que utilizará el proveedor de miniaturas para mostrar la miniatura.|
|[CDocument::GetTitle](#gettitle)|Devuelve el título del documento.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.|
|[CDocument::IsModified](#ismodified)|Indica si el documento se ha modificado desde la última vez que se guardó.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indica si esta `CDocument` instancia de objeto se creó para Search & Organize controlador.|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Se llama para cargar datos de documentos desde la secuencia.|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Se llama antes de cambiar la fuente Rich Preview.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Se llama después de agregar o quitar una vista del documento.|
|[CDocument::OnCloseDocument](#onclosedocument)|Se llama para cerrar el documento.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Llamado por el marco de trabajo cuando necesita crear un marco de vista previa para vista previa enriquecida.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Llamado por el marco de trabajo en respuesta a un evento de documento.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Invalide este método en una clase derivada para dibujar contenido de miniatura.|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Llamado por el marco de trabajo cuando necesita cargar los datos del documento desde la secuencia.|
|[CDocument::OnNewDocument](#onnewdocument)|Se llama para crear un nuevo documento.|
|[CDocument::OnOpenDocument](#onopendocument)|Se llama para abrir un documento existente.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Dirige el controlador de vista previa para devolver el HWND de llamar a la función GetFocus.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Dirige el controlador de vista previa para controlar una pulsación de tecla que se pasa desde la bomba de mensajes del proceso en el que se ejecuta el controlador de vista previa.|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Se llama cuando el color de fondo de Vista previa enriquecida ha cambiado.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Se llama cuando la fuente Rich Preview ha cambiado.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Se llama cuando el sitio de vista previa enriquecida ha cambiado.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Se llama cuando el color del texto de Vista previa enriquecida ha cambiado.|
|[CDocument::OnSaveDocument](#onsavedocument)|Se llama para guardar el documento en el disco.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Llamado por el marco de trabajo cuando se descarga el controlador de vista previa.|
|[CDocument::PreCloseFrame](#precloseframe)|Se llama antes de que se cierre la ventana de marco.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Lee el siguiente valor de fragmento.|
|[CDocument::ReleaseFile](#releasefile)|Libera un archivo para que esté disponible para su uso por otras aplicaciones.|
|[CDocument::RemoveChunk](#removechunk)|Quita un fragmento con GUID especificado.|
|[CDocument::RemoveView](#removeview)|Separa una vista del documento.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Avanzado reemplazable; cuando no se puede completar una operación de abrir o guardar debido a una excepción.|
|[CDocument::SaveModified](#savemodified)|Avanzado reemplazable; llamado para preguntar al usuario si el documento debe ser guardado.|
|[CDocument::SetChunkValue](#setchunkvalue)|Establece un valor de fragmento.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Establece una marca que indica que ha modificado el documento desde la última vez que se guardó.|
|[CDocument::SetPathName](#setpathname)|Establece la ruta de acceso del archivo de datos utilizado por el documento.|
|[CDocument::SetTitle](#settitle)|Establece el título del documento.|
|[CDocument::UpdateAllViews](#updateallviews)|Notifica a todas las vistas que el documento se ha modificado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Envía un mensaje de correo con el documento adjunto.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Habilita el comando Enviar correo si hay compatibilidad con correo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Especifica que `CDocument` el objeto fue creado por dllhost para miniaturas. Debe registrarse `CView::OnDraw`en .|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Especifica que `CDocument` el objeto se creó mediante prevhost para `Rich Preview`. Debe registrarse `CView::OnDraw`en .|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Especifica que `CDocument` el indizador u otra aplicación de búsqueda creó ese objeto.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Especifica el color de fondo de la ventana Vista previa enriquecida. Este color lo establece el host.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Especifica el color de primer plano de la ventana Vista previa enriquecida. Este color lo establece el host.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Especifica la fuente de texto para la ventana Vista previa enriquecida. Esta información de fuente la establece host.|

## <a name="remarks"></a>Observaciones

Un documento representa la unidad de datos que el usuario abre normalmente con el comando Abrir archivo y se guarda con el comando Guardar archivo.

`CDocument`admite operaciones estándar como crear un documento, cargarlo y guardarlo. El marco de trabajo manipula `CDocument`documentos mediante la interfaz definida por .

Una aplicación puede admitir más de un tipo de documento; por ejemplo, una aplicación podría admitir tanto hojas de cálculo como documentos de texto. Cada tipo de documento tiene una plantilla de documento asociada; la plantilla de documento especifica qué recursos (por ejemplo, menú, icono o tabla de aceleradores) se utilizan para ese tipo de documento. Cada documento contiene un `CDocTemplate` puntero a su objeto asociado.

Los usuarios interactúan con un documento a través de los objetos [CView](../../mfc/reference/cview-class.md) asociados a él. Una vista representa una imagen del documento en una ventana de marco e interpreta la entrada del usuario como operaciones en el documento. Un documento puede tener varias vistas asociadas. Cuando el usuario abre una ventana en un documento, el marco de trabajo crea una vista y la adjunta al documento. La plantilla de documento especifica qué tipo de vista y ventana de marco se utilizan para mostrar cada tipo de documento.

Los documentos forman parte del enrutamiento de comandos estándar del marco de trabajo y, en consecuencia, reciben comandos de componentes de interfaz de usuario estándar (como el elemento de menú Guardar archivo). Un documento recibe comandos reenviados por la vista activa. Si el documento no controla un comando determinado, reenvía el comando a la plantilla de documento que lo administra.

Cuando se modifican los datos de un documento, cada una de sus vistas debe reflejar esas modificaciones. `CDocument`proporciona el [UpdateAllViews](#updateallviews) función miembro para notificar a las vistas de estos cambios, por lo que las vistas pueden volver a pintarse según sea necesario. El marco de trabajo también solicita al usuario que guarde un archivo modificado antes de cerrarlo.

Para implementar documentos en una aplicación típica, debe hacer lo siguiente:

- Derive una `CDocument` clase de para cada tipo de documento.

- Agregue variables miembro para almacenar los datos de cada documento.

- Implementar funciones miembro para leer y modificar los datos del documento. Las vistas del documento son los usuarios más importantes de estas funciones miembro.

- Invalide la función miembro [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) en la clase de documento para escribir y leer los datos del documento hacia y desde el disco.

`CDocument`admite el envío de su documento por correo si el soporte de correo (MAPI) está presente. Consulte los artículos Compatibilidad con [MAPI](../../mfc/mapi.md) y [MAPI en MFC](../../mfc/mapi-support-in-mfc.md).

Para obtener `CDocument`más información sobre , vea [Serialización](../../mfc/serialization-in-mfc.md), Temas de arquitectura de [documento/vista](../../mfc/document-view-architecture.md)y Creación de [documentos/vistas](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a>CDocument::AddView

Llame a esta función para adjuntar una vista al documento.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Apunta a la vista que se va a agregar.

### <a name="remarks"></a>Observaciones

Esta función agrega la vista especificada a la lista de vistas asociadas al documento; la función también establece el puntero del documento de la vista a este documento. El marco de trabajo llama a esta función al asociar un objeto de vista recién creado a un documento; esto ocurre en respuesta a un comando Archivo nuevo, Abrir archivo o Nueva ventana o cuando se divide una ventana divisora.

Llame a esta función solo si está creando y adjuntando manualmente una vista. Normalmente, permitirá que el marco de trabajo conecte documentos y vistas definiendo un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, clase de vista y clase de ventana de marco.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::BeginReadChunks

Inicializa la lectura de fragmentos.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument::CanCloseFrame

Llamado por el marco de trabajo antes de que se cierre una ventana de marco que muestra el documento.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
Apunta a la ventana de marco de una vista adjunta al documento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro cerrar la ventana de marco; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada comprueba si hay otras ventanas de marco que muestran el documento. Si la ventana de marco especificada es la última que muestra el documento, la función solicita al usuario que guarde el documento si se ha modificado. Reemplace esta función si desea realizar un procesamiento especial cuando se cierra una ventana de marco. Este es un avanzado reemplazable.

## <a name="cdocumentcdocument"></a><a name="cdocument"></a>CDocument::CDocument

Construye un objeto `CDocument`.

```
CDocument();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo controla la creación de documentos por usted. Invalidar el [OnNewDocument](#onnewdocument) función miembro para realizar la inicialización por documento; esto es particularmente importante en aplicaciones de interfaz de documento único (SDI).

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument::ClearChunkList

Borra la lista de fragmentos.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument::ClearPathName

Borra la ruta de acceso del objeto de documento.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Observaciones

Borrar la ruta `CDocument` de acceso de un objeto hace que la aplicación solicite al usuario cuando se guarde el documento. Esto hace que un comando **Guardar** se comporte como un comando **Guardar como.**

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::DeleteContents

Llamado por el marco de trabajo para eliminar `CDocument` los datos del documento sin destruir el propio objeto.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Observaciones

Se llama justo antes de que el documento sea destruido. También se llama para asegurarse de que un documento está vacío antes de reutilizarlo. Esto es particularmente importante para una aplicación SDI, que utiliza un solo documento; el documento se reutiliza cada vez que el usuario crea o abre otro documento. Llame a esta función para implementar un comando "Editar Borrar todo" o similar que elimine todos los datos del documento. La implementación predeterminada de esta función no hace nada. Reemplace esta función para eliminar los datos del documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::FindChunk

Busca un fragmento con un GUID especificado.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parámetros

*Guid*<br/>
Especifica el GUID de un fragmento que se va a buscar.

*Pid*<br/>
Especifica un PID de un fragmento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Posición en la lista de fragmentos interna si se realiza correctamente. De lo contrario NULL.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::GetAdapter

Devuelve un puntero a `IDocument` un objeto que implementa la interfaz.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `IDocument` que implementa la interfaz.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::GetDocTemplate

Llame a esta función para obtener un puntero a la plantilla de documento para este tipo de documento.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la plantilla de documento para este tipo de documento, o NULL si el documento no está administrado por una plantilla de documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a>CDocument::GetFile

Llame a esta función miembro `CFile` para obtener un puntero a un objeto.

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
Puntero a un objeto de excepción de archivo existente que indica el estado de finalización de la operación.

*nOpenFlags*<br/>
Modo de acceso y uso compartido. Especifica la acción que se debe realizar al abrir el archivo. Puede combinar las opciones enumeradas en el Constructor [CFile CFile::CFile](../../mfc/reference/cfile-class.md#cfile) mediante el operador OR (&#124;) bit a bit. Se requiere un permiso de acceso y una opción de recurso compartido; los `modeCreate` `modeNoInherit` modos y son opcionales.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CFile` .

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition

Llame a esta función para obtener la posición de la primera vista en la lista de vistas asociadas con el documento.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un POSITION valor que se puede utilizar para la iteración con el [GetNextView](#getnextview) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::GetNextView

Llame a esta función para recorrer en iteración todas las vistas del documento.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*rPosición*<br/>
Una referencia a un POSITION valor devuelto `GetNextView` por una llamada anterior a la o [GetFirstViewPosition](#getfirstviewposition) funciones miembro. Este valor no debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Puntero a la vista identificada por *rPosition*.

### <a name="remarks"></a>Observaciones

La función devuelve la vista identificada por *rPosition* y, a continuación, establece *rPosition* en el valor POSITION de la siguiente vista de la lista. Si la vista recuperada es la última de la lista, *rPosition* se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::GetPathName

Llame a esta función para obtener la ruta de acceso completa del archivo de disco del documento.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta completa del documento. Esta cadena está vacía si el documento no se ha guardado o no tiene un archivo de disco asociado.

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::GetThumbnail

Crea un mapa de bits que utilizará el proveedor de miniaturas para mostrar la miniatura.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parámetros

*Cx*<br/>
Especifica el ancho y el alto del mapa de bits.

*phbmp*<br/>
Contiene un identificador de un mapa de bits, cuando la función se devuelve correctamente.

*pdwAlpha*<br/>
Contiene un DWORD que especifica el valor del canal alfa, cuando la función devuelve correctamente.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se creó correctamente un mapa de bits para la miniatura; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentgettitle"></a><a name="gettitle"></a>CDocument::GetTitle

Llame a esta función para obtener el título del documento, que normalmente se deriva del nombre de archivo del documento.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Valor devuelto

El título del documento.

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::InitializeSearchContent

Se llama para inicializar el contenido de búsqueda para el controlador de búsqueda.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para inicializar el contenido de búsqueda. El contenido debe ser una cadena con partes delimitadas por ";". Por ejemplo, "punto; rectángulo; ole".

## <a name="cdocumentismodified"></a><a name="ismodified"></a>CDocument::IsModified

Llame a esta función para determinar si el documento se ha modificado desde la última vez que se guardó.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se ha modificado desde la última vez que se guardó; de lo contrario 0.

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler

Indica si esta `CDocument` instancia de se creó para el controlador de búsqueda & Organizar.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si `CDocument` se creó esta instancia de para el controlador de búsqueda & Organizar.

### <a name="remarks"></a>Observaciones

Actualmente, esta función devuelve TRUE solo para los controladores de vista previa enriquecida implementados en un servidor fuera de proceso. Puede establecer los indicadores adecuados (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) en el nivel de aplicación para que esta función devuelva TRUE.

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream

Se llama para cargar datos de documentos desde una secuencia.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
Un puntero a una secuencia. El Shell proporciona esta secuencia.

*dwGrfMode*<br/>
Modo de acceso a la secuencia.

### <a name="return-value"></a>Valor devuelto

S_OK si la operación de carga se realiza correctamente, de lo contrario HRESULT con un código de error.

### <a name="remarks"></a>Observaciones

Puede invalidar este método en una clase derivada para personalizar cómo cargar datos desde la secuencia.

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode

Especifica que `CDocument` el objeto fue creado por dllhost para miniaturas. Debe registrarse `CView::OnDraw`en .

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Observaciones

`TRUE`indica que el documento fue creado por dllhost para miniaturas.

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode

Especifica que `CDocument` el objeto se creó mediante prevhost para vista previa enriquecida. Debe registrarse `CView::OnDraw`en .

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Observaciones

TRUE indica que el documento se creó mediante prevhost para vista previa enriquecida.

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>CDocument::m_bSearchMode

Especifica que `CDocument` el objeto fue creado por el indizador o por otra aplicación de búsqueda.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Observaciones

`TRUE`indica que el documento fue creado por el indexador o por otra aplicación de búsqueda.

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor

Especifica el color de fondo de la ventana Vista previa enriquecida. Este color lo establece el host.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor

Especifica el color de primer plano de la ventana Vista previa enriquecida. Este color lo establece el host.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont

Especifica la fuente de texto para la ventana Vista previa enriquecida. Esta información de fuente la establece host.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged

Se llama antes de cambiar la fuente Vista previa enriquecida.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument::OnChangedViewList

Llamado por el marco de trabajo después de agregar o quitar una vista del documento.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función comprueba si se está quitando la última vista y, si es así, elimina el documento. Invalide esta función si desea realizar un procesamiento especial cuando el marco de trabajo agrega o quita una vista. Por ejemplo, si desea que un documento permanezca abierto incluso cuando no haya vistas asociadas, reemplace esta función.

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument::OnCloseDocument

Llamado por el marco de trabajo cuando se cierra el documento, normalmente como parte del comando Cierre de archivo.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función destruye todos los marcos utilizados para ver el documento, cierra la vista, limpia el contenido del documento y, a continuación, llama a la [DeleteContents](#deletecontents) función miembro para eliminar los datos del documento.

Invalide esta función si desea realizar un procesamiento de limpieza especial cuando el marco de trabajo cierra un documento. Por ejemplo, si el documento representa un registro en una base de datos, es posible que desee invalidar esta función para cerrar la base de datos. Debe llamar a la versión de clase base de esta función desde la invalidación.

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame

Llamado por el marco de trabajo cuando necesita crear un marco de vista previa para vista previa enriquecida.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el marco se crea correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument::OnDocumentEvent

Llamado por el marco de trabajo en respuesta a un evento de documento.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parámetros

*deEvent*<br/>
[en] Un tipo de datos enumerado que describe el tipo de evento.

### <a name="remarks"></a>Observaciones

Los eventos de documento pueden afectar a varias clases. Este método es responsable de controlar los eventos de documento que afectan a clases distintas de la [clase CDocument](../../mfc/reference/cdocument-class.md). Actualmente, la única clase que debe responder a eventos de documento es la [clase CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). La `CDocument` clase tiene otros métodos reemplazables `CDocument`responsables de controlar el efecto en el archivo .

En la tabla siguiente se enumeran los valores posibles para *deEvent* y los eventos a los que corresponden.

|Value|Evento correspondiente|
|-----------|-------------------------|
|`onAfterNewDocument`|Se ha creado un nuevo documento.|
|`onAfterOpenDocument`|Se abrió un nuevo documento.|
|`onAfterSaveDocument`|El documento se ha guardado.|
|`onAfterCloseDocument`|El documento estaba cerrado.|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail

Invalide este método en una clase derivada para dibujar la miniatura.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
Una referencia a un contexto de dispositivo.

*lprcBounds*<br/>
Especifica un rectángulo delimitador del área donde se debe dibujar la miniatura.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument::OnFileSendMail

Envía un mensaje a través del host de correo residente (si existe) con el documento como archivo adjunto.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Observaciones

`OnFileSendMail`llama a [OnSaveDocument](#onsavedocument) para serializar (guardar) documentos sin título y modificados en un archivo temporal, que luego se envía por correo electrónico. Si el documento no se ha modificado, no se necesita un archivo temporal; se envía el original. `OnFileSendMail`carga MAPI32. DLL si aún no se ha cargado.

Una implementación `OnFileSendMail` especial de [COleDocument](../../mfc/reference/coledocument-class.md) controla los archivos compuestos correctamente.

`CDocument`admite el envío de su documento por correo si el soporte de correo (MAPI) está presente. Vea los artículos [Temas MAPI](../../mfc/mapi.md) y compatibilidad con MAPI [en MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream

Llamado por el marco de trabajo cuando necesita cargar los datos del documento desde una secuencia.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
Un puntero a una secuencia entrante.

*grfMode*<br/>
Modo de acceso a la secuencia.

### <a name="return-value"></a>Valor devuelto

S_OK si la carga se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument::OnNewDocument

Llamado por el marco de trabajo como parte del comando Archivo nuevo.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se inicializó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a la [DeleteContents](#deletecontents) función miembro para asegurarse de que el documento está vacío y, a continuación, marca el nuevo documento como limpio. Invalide esta función para inicializar la estructura de datos de un nuevo documento. Debe llamar a la versión de clase base de esta función desde la invalidación.

Si el usuario elige el comando Archivo nuevo en una aplicación SDI, el marco de trabajo utiliza esta función para reinicializar el documento existente, en lugar de crear uno nuevo. Si el usuario elige Archivo nuevo en una aplicación de interfaz de varios documentos (MDI), el marco de trabajo crea un nuevo documento cada vez y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización en esta función en lugar de en el constructor para que el comando Nuevo archivo sea eficaz en aplicaciones SDI.

Tenga en cuenta `OnNewDocument` que hay casos en los que se llama dos veces. Esto ocurre cuando el documento está incrustado como un servidor de documentos ActiveX. El método llama primero `CreateInstance` a la `COleObjectFactory`función (expuesto por la clase `InitNew` derivada) y `COleServerDoc`una segunda vez por el método (expuesto por la clase derivada).

### <a name="example"></a>Ejemplo

En los ejemplos siguientes se ilustran métodos alternativos para inicializar un objeto de documento.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument::OnOpenDocument

Llamado por el marco de trabajo como parte del comando Abrir archivo.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Señala la ruta del documento que se va a abrir.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se cargó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función abre el archivo especificado, llama a la [DeleteContents](#deletecontents) función miembro para asegurarse de que el documento está vacío, llama a [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) para leer el contenido del archivo y, a continuación, marca el documento como limpio. Invalide esta función si desea utilizar algo distinto del mecanismo de archivado o el mecanismo de archivo. Por ejemplo, puede escribir una aplicación donde los documentos representan registros en una base de datos en lugar de archivos independientes.

Si el usuario elige el comando Abrir archivo en una aplicación SDI, `CDocument` el marco de trabajo utiliza esta función para reinicializar el objeto existente, en lugar de crear uno nuevo. Si el usuario elige File Open en una aplicación MDI, el marco de trabajo construye un nuevo `CDocument` objeto cada vez y, a continuación, llama a esta función para inicializarlo. Debe colocar el código de inicialización en esta función en lugar de en el constructor para que el comando Abrir archivo sea eficaz en aplicaciones SDI.

### <a name="example"></a>Ejemplo

En los ejemplos siguientes se ilustran métodos alternativos para inicializar un objeto de documento.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus

Dirige el controlador de vista previa para devolver `GetFocus` el HWND recuperado de llamar a la función.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parámetros

*phwnd*<br/>
[fuera] Cuando se devuelve este método, contiene un puntero `GetFocus` a la HWND devuelto al llamar a la función desde el subproceso en primer plano del controlador de vista previa.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente; o un valor de error en caso contrario.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator

Dirige el controlador de vista previa para controlar una pulsación de tecla que se pasa desde la bomba de mensajes del proceso en el que se ejecuta el controlador de vista previa.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
[en] Un puntero a un mensaje de ventana.

### <a name="return-value"></a>Valor devuelto

Si el controlador de vista previa puede procesar el mensaje de pulsación de tecla, el controlador lo procesa y devuelve S_OK. Si el controlador de vista previa no puede procesar `IPreviewHandlerFrame::TranslateAccelerator`el mensaje de pulsación de tecla, lo ofrece al host a través de . Si el host procesa el mensaje, este método devuelve S_OK. Si el host no procesa el mensaje, este método devuelve S_FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged

Se llama cuando el color de fondo de vista previa enriquecida ha cambiado.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged

Se llama cuando la fuente Vista previa enriquecida ha cambiado.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged

Se llama cuando el sitio de vista previa enriquecida ha cambiado.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged

Se llama cuando el color del texto vista previa enriquecida ha cambiado.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument::OnSaveDocument

Llamado por el marco de trabajo como parte del comando Guardar archivo o Guardar como archivo.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Señala a la ruta de acceso completa en la que se debe guardar el archivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el documento se guardó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función abre el archivo especificado, llama a [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) para escribir los datos del documento en el archivo y, a continuación, marca el documento como limpio. Reemplace esta función si desea realizar un procesamiento especial cuando el marco de trabajo guarda un documento. Por ejemplo, puede escribir una aplicación donde los documentos representan registros en una base de datos en lugar de archivos independientes.

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument::OnUnloadHandler

Llamado por el marco de trabajo cuando se descarga el controlador de vista previa.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail

Habilita el comando ID_FILE_SEND_MAIL si está presente la compatibilidad con correo (MAPI).

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero al objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) asociado al comando ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Observaciones

De lo contrario, la función elimina el comando ID_FILE_SEND_MAIL del menú, incluidos los separadores situados encima o debajo del elemento de menú según corresponda. MAPI está habilitado si MAPI32. DLL está presente en la ruta de acceso y, en la sección [Mail] de WIN. InI, MAPI-1. La mayoría de las aplicaciones colocan este comando en el menú Archivo.

`CDocument`admite el envío de su documento por correo si el soporte de correo (MAPI) está presente. Vea los artículos [Temas MAPI](../../mfc/mapi.md) y compatibilidad con MAPI [en MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::PreCloseFrame

El marco de trabajo llama a esta función miembro antes de que se destruya la ventana de marco.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
Puntero a la [CFrameWnd](../../mfc/reference/cframewnd-class.md) que `CDocument` contiene el objeto asociado.

### <a name="remarks"></a>Observaciones

Se puede invalidar para proporcionar una limpieza personalizada, pero asegúrese de llamar a la clase base también.

El valor `PreCloseFrame` predeterminado `CDocument`de no hace nada en . Las `CDocument`clases derivadas [COleDocument](../../mfc/reference/coledocument-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utilizan esta función miembro.

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue

Lee el siguiente valor de fragmento.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parámetros

*ppValue*<br/>
[fuera] Cuando se devuelve la función, *ppValue* contiene el valor que se leyó.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::ReleaseFile

El marco de trabajo llama a esta función miembro para liberar un archivo, por lo que está disponible para su uso por otras aplicaciones.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Un puntero a la CFile objeto que se va a liberar.

*bAbort*<br/>
Especifica si el archivo se va `CFile::Close` a `CFile::Abort`liberar mediante uno o . FALSE si el archivo se va a liberar mediante [CFile::Close](../../mfc/reference/cfile-class.md#close); TRUESi el archivo se va a liberar mediante [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Observaciones

Si *bAbort* es `ReleaseFile` `CFile::Abort`TRUE, llama a y se libera el archivo. `CFile::Abort`no lanzará una excepción.

Si *bAbort* es `ReleaseFile` `CFile::Close` FALSE, se liberan las llamadas y el archivo.

Invalide esta función miembro para requerir una acción del usuario antes de que se libere el archivo.

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::RemoveChunk

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

### <a name="remarks"></a>Observaciones

## <a name="cdocumentremoveview"></a><a name="removeview"></a>CDocument::RemoveView

Llame a esta función para separar una vista de un documento.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parámetros

*pView*<br/>
Apunta a la vista que se va a eliminar.

### <a name="remarks"></a>Observaciones

Esta función elimina la vista especificada de la lista de vistas asociadas al documento; también establece el puntero del documento de la vista en NULL. El marco de trabajo llama a esta función cuando se cierra una ventana de marco o se cierra un panel de una ventana divisora.

Llame a esta función solo si está desasociando manualmente una vista. Normalmente, permitirá que el marco de trabajo desasocie documentos y vistas mediante la definición de un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto para asociar una clase de documento, clase de vista y clase de ventana de marco.

Vea el ejemplo en [AddView](#addview) para obtener una implementación de ejemplo.

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException

Se llama si se produce una excepción (normalmente una [CFileException](../../mfc/reference/cfileexception-class.md) o [CArchiveException](../../mfc/reference/carchiveexception-class.md)) al guardar o cargar el documento.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Señala el nombre del documento que se estaba guardando o cargando.

*e*<br/>
Señala la excepción que se ha producido. Puede ser NULL.

*bAhorro*<br/>
Indicador que indica qué operación estaba en curso; distinto de cero si el documento se estaba guardando, 0 si se estaba cargando el documento.

*nIDPDefault*<br/>
Identificador del mensaje de error que se mostrará si la función no especifica uno más específico.

### <a name="remarks"></a>Observaciones

La implementación predeterminada examina el objeto de excepción y busca un mensaje de error que describa específicamente la causa. Si no se encuentra un mensaje específico o si *e* es NULL, se utiliza el mensaje general especificado por el parámetro *nIDPDefault.* A continuación, la función muestra un cuadro de mensaje que contiene el mensaje de error. Invalide esta función si desea proporcionar mensajes de error personalizados adicionales. Este es un avanzado reemplazable.

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a>CDocument::SaveModified

Llamado por el marco de trabajo antes de que se cierre un documento modificado.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro continuar y cerrar el documento; 0 si el documento no debe cerrarse.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función muestra un cuadro de mensaje que pregunta al usuario si desea guardar los cambios en el documento, si se han realizado. Reemplace esta función si el programa requiere un procedimiento de solicitud diferente. Este es un avanzado reemplazable.

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::SetChunkValue

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

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::SetModifiedFlag

Llame a esta función después de haber realizado modificaciones en el documento.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parámetros

*bModificado*<br/>
Marcador que indica si se ha modificado el documento.

### <a name="remarks"></a>Observaciones

Al llamar a esta función de forma coherente, se asegura de que el marco de trabajo solicita al usuario que guarde los cambios antes de cerrar un documento. Normalmente debe usar el valor predeterminado de TRUE para el *bModified* parámetro. Para marcar un documento como limpio (sin modificar), llame a esta función con un valor de FALSE.

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::SetPathName

Llame a esta función para especificar la ruta de acceso completa del archivo de disco del documento.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Apunta a la cadena que se utilizará como ruta de acceso para el documento.

*bAddToMRU*<br/>
Determina si el nombre de archivo se agrega a la lista de archivos (MRU) utilizada más recientemente. Si es TRUE, se agrega el nombre de archivo; si FALSE, no se agrega.

### <a name="remarks"></a>Observaciones

Dependiendo del valor de *bAddToMRU,* la ruta de acceso se agrega, o no se agrega, a la lista MRU mantenida por la aplicación. Tenga en cuenta que algunos documentos no están asociados a un archivo de disco. Llame a esta función solo si va a reemplazar la implementación predeterminada para abrir y guardar los archivos utilizados por el marco de trabajo.

## <a name="cdocumentsettitle"></a><a name="settitle"></a>CDocument::SetTitle

Llame a esta función para especificar el título del documento (la cadena que se muestra en la barra de título de una ventana de marco).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
Señala la cadena que se utilizará como título del documento.

### <a name="remarks"></a>Observaciones

Al llamar a esta función se actualizan los títulos de todas las ventanas de marco que muestran el documento.

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument::UpdateAllViews

Llame a esta función después de modificar el documento.

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

Debe llamar a esta función después de llamar a la [SetModifiedFlag](#setmodifiedflag) función miembro. Esta función informa a cada vista adjunta al documento, excepto a la vista especificada por *pSender*, que el documento se ha modificado. Normalmente se llama a esta función desde la clase de vista después de que el usuario ha cambiado el documento a través de una vista.

Esta función llama a la Función miembro [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) para cada una de las vistas del documento excepto la vista de envío, pasando *pHint* y *lHint*. Utilice estos parámetros para pasar información a las vistas sobre las modificaciones realizadas en el documento. Puede codificar información mediante *lHint* y/o puede definir una clase derivada de [CObject](../../mfc/reference/cobject-class.md)para almacenar información sobre las modificaciones y pasar un objeto de esa clase mediante *pHint*. Invalidar `CView::OnUpdate` la función miembro en [el CView](../../mfc/reference/cview-class.md)-clase derivada para optimizar la actualización de la presentación de la vista en función de la información pasada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[EJEMPLO de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[NPP de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)
