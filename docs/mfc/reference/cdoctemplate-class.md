---
title: CDocTemplate (clase)
ms.date: 11/04/2016
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
ms.openlocfilehash: 3b2d84af9be8e5c606cde8794b51e12207dcdec9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426076"
---
# <a name="cdoctemplate-class"></a>CDocTemplate (clase)

Una clase base abstracta que define la funcionalidad básica para las plantillas de documento.

## <a name="syntax"></a>Sintaxis

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDocTemplate:: CDocTemplate](#cdoctemplate)|Construye un objeto `CDocTemplate`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocTemplate:: AddDocument](#adddocument)|Agrega un documento a una plantilla.|
|[CDocTemplate:: CloseAllDocuments](#closealldocuments)|Cierra todos los documentos asociados a esta plantilla.|
|[CDocTemplate:: CreateNewDocument](#createnewdocument)|Crea un nuevo documento.|
|[CDocTemplate:: CreateNewFrame](#createnewframe)|Crea una nueva ventana de marco que contiene un documento y una vista.|
|[CDocTemplate:: CreateOleFrame](#createoleframe)|Crea una ventana de marco habilitada para OLE.|
|[CDocTemplate:: CreatePreviewFrame](#createpreviewframe)|Crea un marco secundario que se usa para la vista previa enriquecida.|
|[CDocTemplate:: GetDocString](#getdocstring)|Recupera una cadena asociada al tipo de documento.|
|[CDocTemplate:: GetFirstDocPosition](#getfirstdocposition)|Recupera la posición del primer documento asociado a esta plantilla.|
|[CDocTemplate:: GetNextDoc](#getnextdoc)|Recupera un documento y la posición del siguiente.|
|[CDocTemplate:: InitialUpdateFrame](#initialupdateframe)|Inicializa la ventana de marco y, opcionalmente, la hace visible.|
|[CDocTemplate:: LoadTemplate](#loadtemplate)|Carga los recursos para una `CDocTemplate` determinada o una clase derivada.|
|[CDocTemplate:: MatchDocType](#matchdoctype)|Determina el grado de confianza en la coincidencia entre un tipo de documento y esta plantilla.|
|[CDocTemplate:: OpenDocumentFile](#opendocumentfile)|Abre un archivo especificado por una ruta de acceso.|
|[CDocTemplate:: RemoveDocument](#removedocument)|Quita un documento de una plantilla.|
|[CDocTemplate:: SaveAllModified](#saveallmodified)|Guarda todos los documentos asociados a esta plantilla que se han modificado.|
|[CDocTemplate:: SetContainerInfo](#setcontainerinfo)|Determina los recursos de los contenedores OLE al editar un elemento OLE en contexto.|
|[CDocTemplate:: SetDefaultTitle](#setdefaulttitle)|Muestra el título predeterminado en la barra de título de la ventana de documento.|
|[CDocTemplate:: SetPreviewInfo](#setpreviewinfo)|Configura el controlador de vista previa del proceso.|
|[CDocTemplate:: SetServerInfo](#setserverinfo)|Determina los recursos y las clases cuando el documento del servidor se inserta o se edita en contexto.|

## <a name="remarks"></a>Observaciones

Normalmente, se crean una o varias plantillas de documento en la implementación de la función de `InitInstance` de la aplicación. Una plantilla de documento define las relaciones entre tres tipos de clases:

- Una clase de documento, que se deriva de `CDocument`.

- Una clase de vista, que muestra los datos de la clase de documento indicada anteriormente. Puede derivar esta clase de `CView`, `CScrollView`, `CFormView`o `CEditView`. (También puede usar `CEditView` directamente).

- Una clase de ventana de marco que contiene la vista. En el caso de una aplicación de interfaz de un único documento (SDI), se deriva esta clase de `CFrameWnd`. En el caso de una aplicación de interfaz de múltiples documentos (MDI), esta clase se deriva de `CMDIChildWnd`. Si no necesita personalizar el comportamiento de la ventana de marco, puede usar `CFrameWnd` o `CMDIChildWnd` directamente sin derivar su propia clase.

La aplicación tiene una plantilla de documento para cada tipo de documento que admite. Por ejemplo, si la aplicación admite hojas de cálculo y documentos de texto, la aplicación tiene dos objetos de plantilla de documento. Cada plantilla de documento es responsable de la creación y administración de todos los documentos de su tipo.

La plantilla de documento almacena punteros a los objetos de `CRuntimeClass` para las clases de documento, vista y ventana de marco. Estos objetos `CRuntimeClass` se especifican al construir una plantilla de documento.

La plantilla de documento contiene el identificador de los recursos usados con el tipo de documento (por ejemplo, los recursos de menús, iconos o tablas de aceleradores). La plantilla de documento también contiene cadenas que contienen información adicional sobre su tipo de documento. Estos incluyen el nombre del tipo de documento (por ejemplo, "Worksheet") y la extensión de archivo (por ejemplo, ". xls"). Opcionalmente, puede contener otras cadenas usadas por la interfaz de usuario de la aplicación, el administrador de archivos de Windows y la compatibilidad con la vinculación e incrustación de objetos (OLE).

Si la aplicación es un contenedor OLE o un servidor, la plantilla de documento también define el identificador del menú usado durante la activación en contexto. Si la aplicación es un servidor OLE, la plantilla de documento define el identificador de la barra de herramientas y el menú usados durante la activación en contexto. Estos recursos OLE adicionales se especifican mediante una llamada a `SetContainerInfo` y `SetServerInfo`.

Dado que `CDocTemplate` es una clase abstracta, no se puede utilizar directamente la clase. Una aplicación típica usa una de las dos clases derivadas de `CDocTemplate`proporcionadas por el biblioteca MFC: `CSingleDocTemplate`, que implementa SDI y `CMultiDocTemplate`, que implementa MDI. Vea esas clases para obtener más información sobre el uso de plantillas de documento.

Si su aplicación requiere un paradigma de interfaz de usuario que sea fundamentalmente diferente de SDI o MDI, puede derivar su propia clase de `CDocTemplate`.

Para obtener más información sobre `CDocTemplate`, consulte [plantillas de documento y el proceso de creación de documentos y vistas](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="adddocument"></a>CDocTemplate:: AddDocument

Utilice esta función para agregar un documento a una plantilla.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Puntero al documento que se va a agregar.

### <a name="remarks"></a>Observaciones

Las clases derivadas [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) y [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) invalidan esta función. Si deriva su propia clase de plantilla de documento de `CDocTemplate`, la clase derivada debe reemplazar esta función.

##  <a name="cdoctemplate"></a>CDocTemplate:: CDocTemplate

Construye un objeto `CDocTemplate`.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parámetros

*nIDResource*<br/>
Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir el menú, el icono, la tabla de aceleradores y los recursos de cadena.

El recurso de cadena consta de hasta siete subcadenas separadas por el carácter "\n" (se necesita el carácter "\n" como marcador de posición si no se incluye una subcadena; sin embargo, los caracteres "\n" finales no son necesarios); Estas subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, vea [GetDocString](#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Tenga en cuenta que la cadena comienza con un carácter "\n"; Esto se debe a que la primera subcadena no se utiliza para las aplicaciones MDI y, por lo tanto, no se incluye. Puede editar esta cadena con el editor de cadenas; la cadena completa aparece como una sola entrada en el editor de cadenas, no como siete entradas independientes.

*pDocClass*<br/>
Apunta al objeto `CRuntimeClass` de la clase Document. Esta clase es una clase derivada de `CDocument`que se define para representar los documentos.

*pFrameClass*<br/>
Apunta al objeto `CRuntimeClass` de la clase de ventana de marco. Esta clase puede ser una clase derivada de `CFrameWnd`, o bien se puede `CFrameWnd` si desea el comportamiento predeterminado de la ventana de marco principal.

*pViewClass*<br/>
Apunta al objeto `CRuntimeClass` de la clase de vista. Esta clase es una clase derivada de `CView`que se define para mostrar los documentos.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro para construir un objeto de `CDocTemplate`. Asigne dinámicamente un objeto `CDocTemplate` y páselo a [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) desde la función miembro `InitInstance` de la clase de la aplicación.

##  <a name="closealldocuments"></a>CDocTemplate:: CloseAllDocuments

Llame a esta función miembro para cerrar todos los documentos abiertos.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parámetros

*bEndSession*<br/>
No se usa.

### <a name="remarks"></a>Observaciones

Esta función miembro se utiliza normalmente como parte del comando de salida de archivo. La implementación predeterminada de esta función llama a la función miembro [CDocument::D eletecontents](../../mfc/reference/cdocument-class.md#deletecontents) para eliminar los datos del documento y, a continuación, cierra las ventanas de marco para todas las vistas adjuntas al documento.

Invalide esta función si desea exigir al usuario que realice un procesamiento de limpieza especial antes de cerrar el documento. Por ejemplo, si el documento representa un registro en una base de datos, puede que desee invalidar esta función para cerrar la base de datos.

##  <a name="createnewdocument"></a>CDocTemplate:: CreateNewDocument

Llame a esta función miembro para crear un nuevo documento del tipo asociado a esta plantilla de documento.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento recién creado o NULL si se produce un error.

##  <a name="createnewframe"></a>CDocTemplate:: CreateNewFrame

Crea una nueva ventana de marco que contiene un documento y una vista.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Documento al que debe hacer referencia la nueva ventana de marco. Puede ser NULL.

*pOther*<br/>
Ventana de marco en la que se va a basar la nueva ventana de marco. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana de marco recién creada, o NULL si se produce un error.

### <a name="remarks"></a>Observaciones

`CreateNewFrame` utiliza los objetos `CRuntimeClass` pasados al constructor para crear una nueva ventana de marco con una vista y un documento adjuntos. Si el parámetro *pDoc* es null, el marco de trabajo genera un mensaje de seguimiento.

El parámetro *pOther* se usa para implementar el nuevo comando de ventana. Proporciona una ventana de marco en la que se va a modelar la nueva ventana de marco. La nueva ventana de marco se crea normalmente invisible. Llame a esta función para crear ventanas de marco fuera de la implementación del marco estándar de archivo nuevo y abrir archivo.

##  <a name="createoleframe"></a>CDocTemplate:: CreateOleFrame

Crea una ventana de marco OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana primaria del marco.

*pDoc*<br/>
Un puntero al documento al que debe hacer referencia la nueva ventana de marco OLE.

*bCreateView*<br/>
Determina si se crea una vista junto con el marco.

### <a name="return-value"></a>Valor devuelto

Un puntero a una ventana de marco si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Si *bCreateView* es cero, se crea un marco vacío.

##  <a name="getdocstring"></a>CDocTemplate:: GetDocString

Recupera una cadena asociada al tipo de documento.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Referencia a un objeto `CString` que contendrá la cadena cuando la función devuelva un valor.

*índice*<br/>
Índice de la subcadena que se va a recuperar de la cadena que describe el tipo de documento. Este parámetro puede tener uno de los valores siguientes:

- `CDocTemplate::windowTitle` nombre que aparece en la barra de título de la ventana de la aplicación (por ejemplo, "Microsoft Excel"). Presente solo en la plantilla de documento para aplicaciones SDI.

- `CDocTemplate::docName` raíz del nombre de documento predeterminado (por ejemplo, "Sheet"). Esta raíz, más un número, se usa para el nombre predeterminado de un nuevo documento de este tipo cada vez que el usuario elige el nuevo comando en el menú Archivo (por ejemplo, "Hoja1" o "Hoja2"). Si no se especifica, se usa "Untitled" como valor predeterminado.

- `CDocTemplate::fileNewName` nombre de este tipo de documento. Si la aplicación admite más de un tipo de documento, esta cadena se muestra en el cuadro de diálogo archivo nuevo (por ejemplo, "hoja de cálculo"). Si no se especifica, no se puede obtener acceso al tipo de documento mediante el comando archivo nuevo.

- `CDocTemplate::filterName` Descripción del tipo de documento y un filtro comodín que coincida con los documentos de este tipo. Esta cadena se muestra en la lista desplegable Mostrar archivos de tipo en el cuadro de diálogo Abrir archivo (por ejemplo, "hojas de cálculo (*. xls)"). Si no se especifica, no se puede obtener acceso al tipo de documento mediante el comando Abrir archivo.

- `CDocTemplate::filterExt` extensión para los documentos de este tipo (por ejemplo, ". xls"). Si no se especifica, no se puede obtener acceso al tipo de documento mediante el comando Abrir archivo.

- `CDocTemplate::regFileTypeId` identificador del tipo de documento que se va a almacenar en la base de datos de registro que mantiene Windows. Esta cadena solo es para uso interno (por ejemplo, "ExcelWorksheet"). Si no se especifica, el tipo de documento no se puede registrar con el administrador de archivos de Windows.

- `CDocTemplate::regFileTypeName` nombre del tipo de documento que se va a almacenar en la base de datos de registro. Esta cadena se puede mostrar en cuadros de diálogo de aplicaciones que tienen acceso a la base de datos de registro (por ejemplo, "hoja de cálculo de Microsoft Excel").

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la subcadena especificada; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar una subcadena específica que describa el tipo de documento. La cadena que contiene estas subcadenas se almacena en la plantilla de documento y se deriva de una cadena en el archivo de recursos de la aplicación. El marco de trabajo llama a esta función para obtener las cadenas que necesita para la interfaz de usuario de la aplicación. Si ha especificado una extensión de nombre de archivo para los documentos de la aplicación, el marco de trabajo también llama a esta función cuando se agrega una entrada a la base de datos de registro de Windows. Esto permite abrir los documentos desde el administrador de archivos de Windows.

Llame a esta función solo si va a derivar su propia clase de `CDocTemplate`.

##  <a name="getfirstdocposition"></a>CDocTemplate:: GetFirstDocPosition

Recupera la posición del primer documento asociado a esta plantilla.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para recorrer en iteración la lista de documentos asociada a esta plantilla de documento; o NULL si la lista está vacía.

### <a name="remarks"></a>Observaciones

Utilice esta función para obtener la posición del primer documento en la lista de documentos asociados a esta plantilla. Use el valor POSITION como argumento para [CDocTemplate:: GetNextDoc](#getnextdoc) para recorrer en iteración la lista de documentos asociados a la plantilla.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) y [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) invalidan esta función virtual pura. Cualquier clase que derive de `CDocTemplate` también debe invalidar esta función.

##  <a name="getnextdoc"></a>CDocTemplate:: GetNextDoc

Recupera el elemento de lista identificado por *rPos*y, a continuación, establece *rPos* en el valor de posición de la entrada siguiente de la lista.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al siguiente documento en la lista de documentos asociados a esta plantilla.

### <a name="parameters"></a>Parámetros

*Objective*<br/>
Referencia a un valor de posición devuelto por una llamada anterior a [GetFirstDocPosition](#getfirstdocposition) o `GetNextDoc`.

### <a name="remarks"></a>Observaciones

Si el elemento recuperado es el último de la lista, el nuevo valor de *rPos* se establece en NULL.

Puede usar `GetNextDoc` en un bucle de iteración hacia delante si establece la posición inicial con una llamada a [GetFirstDocPosition](#getfirstdocposition).

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, la versión de depuración del biblioteca MFC valida.

##  <a name="initialupdateframe"></a>CDocTemplate:: InitialUpdateFrame

Inicializa la ventana de marco y, opcionalmente, la hace visible.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
La ventana de marco que necesita la actualización inicial.

*pDoc*<br/>
Documento al que está asociado el marco. Puede ser NULL.

*bMakeVisible*<br/>
Indica si el marco debe ser visible y activo.

### <a name="remarks"></a>Observaciones

Llame a `IntitialUpdateFrame` después de crear un nuevo marco con `CreateNewFrame`. La llamada a esta función hace que las vistas de la ventana de marco reciban sus llamadas `OnInitialUpdate`. Además, si no había anteriormente una vista activa, la vista principal de la ventana de marco se activa; la vista principal es una vista con un identificador secundario de AFX_IDW_PANE_FIRST. Por último, la ventana de marco se hace visible si *bMakeVisible* es distinto de cero. Si *bMakeVisible* es cero, el foco actual y el estado visible de la ventana de marco permanecerán sin cambios.

No es necesario llamar a esta función cuando se usa la implementación del archivo New y el archivo Open del marco de trabajo.

##  <a name="loadtemplate"></a>CDocTemplate:: LoadTemplate

Carga los recursos para una `CDocTemplate` determinada o una clase derivada.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para cargar los recursos de una determinada `CDocTemplate` o clase derivada. Normalmente se llama durante la construcción, excepto cuando la plantilla se está construyendo globalmente. En ese caso, la llamada a `LoadTemplate` se retrasa hasta que se llama a [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) .

##  <a name="matchdoctype"></a>CDocTemplate:: MatchDocType

Determina el grado de confianza en la coincidencia entre un tipo de documento y esta plantilla.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Ruta de acceso del archivo cuyo tipo se va a determinar.

*rpDocMatch*<br/>
Puntero a un documento al que se asigna el documento coincidente, si el archivo especificado por *lpszPathName* ya está abierto.

### <a name="return-value"></a>Valor devuelto

Un valor de la enumeración **Confidence** , que se define de la siguiente manera:

```
enum Confidence
    {
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };
```

### <a name="remarks"></a>Observaciones

Utilice esta función para determinar el tipo de plantilla de documento que se va a usar para abrir un archivo. Por ejemplo, si la aplicación admite varios tipos de archivo, puede usar esta función para determinar cuál de las plantillas de documento disponibles es adecuada para un archivo determinado mediante una llamada a `MatchDocType` para cada plantilla a su vez y elegir una plantilla según el valor de confianza devuelto.

Si el archivo especificado por *lpszPathName* ya está abierto, esta función devuelve `CDocTemplate::yesAlreadyOpen` y copia el objeto de `CDocument` del archivo en el objeto en *rpDocMatch*.

Si el archivo no está abierto pero la extensión de *lpszPathName* coincide con la extensión especificada por `CDocTemplate::filterExt`, esta función devuelve `CDocTemplate::yesAttemptNative` y establece *rpDocMatch* en NULL. Para obtener más información sobre `CDocTemplate::filterExt`, vea [CDocTemplate:: GetDocString](#getdocstring).

Si no se cumple ninguna de las mayúsculas y minúsculas, la función devuelve `CDocTemplate::yesAttemptForeign`.

La implementación predeterminada no devuelve `CDocTemplate::maybeAttemptForeign` ni `CDocTemplate::maybeAttemptNative`. Invalide esta función para implementar la lógica de coincidencia de tipos adecuada para su aplicación, quizás usando estos dos valores de la enumeración **Confidence** .

##  <a name="opendocumentfile"></a>CDocTemplate:: OpenDocumentFile

Abre un archivo especificado por una ruta de acceso.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
de Puntero a la ruta de acceso del archivo que contiene el documento que se va a abrir.

*bAddToMRU*<br/>
de TRUE indica que el documento es uno de los archivos más recientes; FALSE indica que el documento no es uno de los archivos más recientes.

### <a name="return-value"></a>Valor devuelto

Un puntero al documento cuyo archivo se denomina *lpszPathName*; NULL si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Abre el archivo cuya ruta de acceso se especifica mediante *lpszPathName*. Si *lpszPathName* es null, se crea un nuevo archivo que contiene un documento del tipo asociado a esta plantilla.

##  <a name="removedocument"></a>CDocTemplate:: RemoveDocument

Quita de la lista de documentos asociados a esta plantilla el documento al que apunta *pDoc* .

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Puntero al documento que se va a quitar.

### <a name="remarks"></a>Observaciones

Las clases derivadas `CMultiDocTemplate` y `CSingleDocTemplate` invalidan esta función. Si deriva su propia clase de plantilla de documento de `CDocTemplate`, la clase derivada debe reemplazar esta función.

##  <a name="saveallmodified"></a>CDocTemplate:: SaveAllModified

Guarda todos los documentos que se han modificado.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es correcto; de lo contrario, es 0.

##  <a name="setcontainerinfo"></a>CDocTemplate:: SetContainerInfo

Determina los recursos de los contenedores OLE al editar un elemento OLE en contexto.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parámetros

*nIDOleInPlaceContainer*<br/>
IDENTIFICADOR de los recursos utilizados cuando se activa un objeto incrustado.

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer los recursos que se usarán cuando un objeto OLE esté activado en contexto. Estos recursos pueden incluir menús y tablas de aceleradores. Normalmente, se llama a esta función en la función [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de la aplicación.

El menú asociado a *nIDOleInPlaceContainer* contiene separadores que permiten combinar el menú del elemento en contexto activado con el menú de la aplicación contenedora. Para obtener más información sobre la combinación de menús de servidor y de contenedor, vea el artículo [menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="setdefaulttitle"></a>CDocTemplate:: SetDefaultTitle

Llame a esta función para cargar el título predeterminado del documento y mostrarlo en la barra de título del documento.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parámetros

*pDocument*<br/>
Puntero al documento cuyo título se va a establecer.

### <a name="remarks"></a>Observaciones

Para obtener información sobre el título predeterminado, vea la descripción de `CDocTemplate::docName` en [CDocTemplate:: GetDocString](#getdocstring).

##  <a name="setserverinfo"></a>CDocTemplate:: SetServerInfo

Determina los recursos y las clases cuando el documento del servidor se inserta o se edita en contexto.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parámetros

*nIDOleEmbedding*<br/>
IDENTIFICADOR de los recursos que se usan cuando se abre un objeto incrustado en una ventana independiente.

*nIDOleInPlaceServer*<br/>
IDENTIFICADOR de los recursos utilizados cuando se activa un objeto incrustado en contexto.

*pOleFrameClass*<br/>
Puntero a una estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que contiene información de clase para el objeto de ventana de marco que se crea cuando se produce la activación en contexto.

*pOleViewClass*<br/>
Puntero a una estructura de `CRuntimeClass` que contiene información de clase para el objeto de vista creado cuando se produce la activación en contexto.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para identificar los recursos que usará la aplicación de servidor cuando el usuario solicite la activación de un objeto incrustado. Estos recursos se componen de menús y tablas de aceleradores. Normalmente, se llama a esta función en la `InitInstance` de la aplicación.

El menú asociado a *nIDOleInPlaceServer* contiene separadores que permiten combinar el menú servidor con el menú del contenedor. Para obtener más información sobre la combinación de menús de servidor y de contenedor, vea el artículo [menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="createpreviewframe"></a>CDocTemplate:: CreatePreviewFrame

Crea un marco secundario que se usa para la vista previa enriquecida.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Un puntero a una ventana primaria (normalmente proporcionado por el shell).

*pDoc*<br/>
Un puntero a un objeto de documento, cuyo contenido se mostrará como vista previa.

### <a name="return-value"></a>Valor devuelto

Puntero válido a un objeto `CFrameWnd`, o NULL si se produce un error en la creación.

### <a name="remarks"></a>Observaciones

##  <a name="setpreviewinfo"></a>CDocTemplate:: SetPreviewInfo

Configura el controlador de vista previa fuera del proceso.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parámetros

*nIDPreviewFrame*<br/>
Especifica un identificador de recurso del marco de vista previa.

*pPreviewFrameClass*<br/>
Especifica un puntero a una estructura de información de clase en tiempo de ejecución del marco de vista previa.

*pPreviewViewClass*<br/>
Especifica un puntero a una estructura de información de clase en tiempo de ejecución de la vista previa.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate (clase)](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate (clase)](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CScrollView (clase)](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView (clase)](../../mfc/reference/ceditview-class.md)<br/>
[CFormView (clase)](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
