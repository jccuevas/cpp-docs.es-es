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
ms.openlocfilehash: 69b94a4188804f47c950ca31fb5cba80d85176e9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753300"
---
# <a name="cdoctemplate-class"></a>CDocTemplate (clase)

Una clase base abstracta que define la funcionalidad básica para las plantillas de documento.

## <a name="syntax"></a>Sintaxis

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Construye un objeto `CDocTemplate`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocTemplate::AddDocument](#adddocument)|Agrega un documento a una plantilla.|
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Cierra todos los documentos asociados a esta plantilla.|
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Crea un nuevo documento.|
|[CDocTemplate::CreateNewFrame](#createnewframe)|Crea una nueva ventana de marco que contiene un documento y una vista.|
|[CDocTemplate::CreateOleFrame](#createoleframe)|Crea una ventana de marco habilitada para OLE.|
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Crea un marco secundario utilizado para la vista previa enriquecida.|
|[CDocTemplate::GetDocString](#getdocstring)|Recupera una cadena asociada al tipo de documento.|
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Recupera la posición del primer documento asociado a esta plantilla.|
|[CDocTemplate::GetNextDoc](#getnextdoc)|Recupera un documento y la posición del siguiente.|
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicializa la ventana de marco y, opcionalmente, la hace visible.|
|[CDocTemplate::LoadTemplate](#loadtemplate)|Carga los recursos `CDocTemplate` de una clase determinada o derivada.|
|[CDocTemplate::MatchDocType](#matchdoctype)|Determina el grado de confianza en la coincidencia entre un tipo de documento y esta plantilla.|
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Abre un archivo especificado por un nombre de ruta.|
|[CDocTemplate::RemoveDocument](#removedocument)|Quita un documento de una plantilla.|
|[CDocTemplate::SaveAllModified](#saveallmodified)|Guarda todos los documentos asociados a esta plantilla que se han modificado.|
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Determina los recursos de los contenedores OLE al editar un elemento OLE en contexto.|
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Muestra el título predeterminado en la barra de título de la ventana del documento.|
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Configuraciones fuera del proceso de controlador de vista previa.|
|[CDocTemplate::SetServerInfo](#setserverinfo)|Determina los recursos y las clases cuando el documento del servidor se incrusta o edita in situ.|

## <a name="remarks"></a>Observaciones

Normalmente se crean una o varias plantillas de `InitInstance` documento en la implementación de la función de la aplicación. Una plantilla de documento define las relaciones entre tres tipos de clases:

- Una clase de documento, `CDocument`de la que se deriva .

- Una clase de vista, que muestra los datos de la clase de documento enumerada anteriormente. Puede derivar esta `CView`clase `CScrollView` `CFormView`de `CEditView`, , , o . (También puede `CEditView` utilizar directamente.)

- Una clase de ventana de marco, que contiene la vista. Para una aplicación de interfaz de documento único `CFrameWnd`(SDI), se deriva esta clase de . Para una aplicación de interfaz de varios documentos (MDI), se deriva esta clase de `CMDIChildWnd`. Si no necesita personalizar el comportamiento de la ventana `CFrameWnd` de `CMDIChildWnd` marco, puede usar la ventana o directamente sin derivar su propia clase.

La aplicación tiene una plantilla de documento para cada tipo de documento que admite. Por ejemplo, si la aplicación admite hojas de cálculo y documentos de texto, la aplicación tiene dos objetos de plantilla de documento. Cada plantilla de documento es responsable de crear y administrar todos los documentos de su tipo.

La plantilla de documento `CRuntimeClass` almacena punteros a los objetos de las clases de ventana de documento, vista y marco. Estos `CRuntimeClass` objetos se especifican al construir una plantilla de documento.

La plantilla de documento contiene el identificador de los recursos utilizados con el tipo de documento (como los recursos de menú, icono o tabla de aceleradores). La plantilla de documento también tiene cadenas que contienen información adicional sobre su tipo de documento. Estos incluyen el nombre del tipo de documento (por ejemplo, "Hoja de trabajo") y la extensión de archivo (por ejemplo, ".xls"). Opcionalmente, puede contener otras cadenas utilizadas por la interfaz de usuario de la aplicación, el Administrador de archivos de Windows y compatibilidad con la vinculación e incrustación de objetos (OLE).

Si la aplicación es un contenedor OLE o un servidor, la plantilla de documento también define el identificador del menú utilizado durante la activación en contexto. Si la aplicación es un servidor OLE, la plantilla de documento define el identificador de la barra de herramientas y el menú utilizados durante la activación en contexto. Especifique estos recursos OLE `SetContainerInfo` adicionales `SetServerInfo`llamando y .

Dado `CDocTemplate` que es una clase abstracta, no puede usar la clase directamente. Una aplicación típica utiliza `CDocTemplate`una de las dos clases derivadas `CSingleDocTemplate`proporcionadas por la `CMultiDocTemplate`biblioteca Microsoft Foundation Class: , que implementa SDI y , que implementa MDI. Consulte esas clases para obtener más información sobre el uso de plantillas de documento.

Si la aplicación requiere un paradigma de interfaz de usuario que sea fundamentalmente `CDocTemplate`diferente de SDI o MDI, puede derivar su propia clase de .

Para obtener `CDocTemplate`más información sobre , consulte Plantillas de documento y Proceso de creación de [documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a>CDocTemplate::AddDocument

Utilice esta función para agregar un documento a una plantilla.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Un puntero al documento que se va a agregar.

### <a name="remarks"></a>Observaciones

Las clases derivadas [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) y [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) invalidan esta función. Si deriva su propia clase `CDocTemplate`de plantilla de documento de , la clase derivada debe invalidar esta función.

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a>CDocTemplate::CDocTemplate

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
Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir menú, icono, tabla de aceleradores y recursos de cadena.

El recurso de cadena consta de hasta siete subcadenas separadas por el carácter ''n' (se necesita el carácter ''n' como un titular de posición si no se incluye una subcadena; sin embargo, no es necesario dejar de caracteres 'n'); estas subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, vea [GetDocString](#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Tenga en cuenta que la cadena comienza con un carácter 'n'; esto se debe a que la primera subcadena no se utiliza para aplicaciones MDI, por lo que no se incluye. Puede editar esta cadena mediante el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadenas, no como siete entradas independientes.

*pDocClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de documento. Esta clase `CDocument`es una clase derivada que se define para representar los documentos.

*pFrameClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede `CFrameWnd`ser una clase derivada, `CFrameWnd` o puede ser en sí misma si desea un comportamiento predeterminado para la ventana de marco principal.

*pViewClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de vista. Esta clase `CView`es una clase derivada que se define para mostrar los documentos.

### <a name="remarks"></a>Observaciones

Utilice esta función `CDocTemplate` miembro para construir un objeto. Asigne dinámicamente `CDocTemplate` un objeto y páselo a [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) desde la función miembro de la `InitInstance` clase de aplicación.

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments

Llame a esta función miembro para cerrar todos los documentos abiertos.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parámetros

*bEndSession*<br/>
No se usa.

### <a name="remarks"></a>Observaciones

Esta función miembro se utiliza normalmente como parte del comando de salida de archivo. La implementación predeterminada de esta función llama a la [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) función miembro para eliminar los datos del documento y, a continuación, cierra las ventanas de marco para todas las vistas adjuntas al documento.

Reemplace esta función si desea que el usuario realice un procesamiento de limpieza especial antes de cerrar el documento. Por ejemplo, si el documento representa un registro en una base de datos, es posible que desee invalidar esta función para cerrar la base de datos.

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a>CDocTemplate::CreateNewDocument

Llame a esta función miembro para crear un nuevo documento del tipo asociado a esta plantilla de documento.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento recién creado, o NULL si se produce un error.

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a>CDocTemplate::CreateNewFrame

Crea una nueva ventana de marco que contiene un documento y una vista.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
El documento al que debe hacer referencia la nueva ventana de marco. Puede ser NULL.

*pOtros*<br/>
La ventana de marco en la que se va a basar la nueva ventana de marco. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de marco recién creada, o NULL si se produce un error.

### <a name="remarks"></a>Observaciones

`CreateNewFrame`utiliza `CRuntimeClass` los objetos pasados al constructor para crear una nueva ventana de marco con una vista y un documento adjuntos. Si el *pDoc* parámetro es NULL, el marco de trabajo genera un mensaje TRACE.

El *pOther* parámetro se utiliza para implementar el window New comando. Proporciona una ventana de marco en la que modelar la nueva ventana de marco. La nueva ventana de marco suele crearse invisible. Llame a esta función para crear ventanas de marco fuera de la implementación de marco estándar de archivo nuevo y archivo abierto.

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a>CDocTemplate::CreateOleFrame

Crea una ventana de marco OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Un puntero a la ventana primaria del marco.

*pDoc*<br/>
Puntero al documento al que debe hacer referencia la nueva ventana de marco OLE.

*bCreateView*<br/>
Determina si se crea una vista junto con el marco.

### <a name="return-value"></a>Valor devuelto

Un puntero a una ventana de marco si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si *bCreateView* es cero, se crea un marco vacío.

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a>CDocTemplate::GetDocString

Recupera una cadena asociada al tipo de documento.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Una referencia `CString` a un objeto que contendrá la cadena cuando se devuelve la función.

*índice*<br/>
Un índice de la subcadena que se recupera de la cadena que describe el tipo de documento. Este parámetro puede tener uno de los valores siguientes:

- `CDocTemplate::windowTitle`Nombre que aparece en la barra de título de la ventana de la aplicación (por ejemplo, "Microsoft Excel"). Presente solo en la plantilla de documento para aplicaciones SDI.

- `CDocTemplate::docName`Raíz para el nombre de documento predeterminado (por ejemplo, "Hoja"). Esta raíz, más un número, se utiliza para el nombre predeterminado de un nuevo documento de este tipo cada vez que el usuario elige el comando Nuevo en el menú Archivo (por ejemplo, "Sheet1" o "Sheet2"). Si no se especifica, "Sin título" se utiliza como valor predeterminado.

- `CDocTemplate::fileNewName`Nombre de este tipo de documento. Si la aplicación admite más de un tipo de documento, esta cadena se muestra en el cuadro de diálogo Nuevo archivo (por ejemplo, "Hoja de trabajo"). Si no se especifica, el tipo de documento es inaccesible mediante el comando Archivo nuevo.

- `CDocTemplate::filterName`Descripción del tipo de documento y un filtro comodín que coincide con documentos de este tipo. Esta cadena se muestra en la lista desplegable Lista de archivos de tipo del cuadro de diálogo Abrir archivo (por ejemplo, "Hojas de trabajo (*.xls)"). Si no se especifica, el tipo de documento es inaccesible mediante el comando Abrir archivo.

- `CDocTemplate::filterExt`Extensión para documentos de este tipo (por ejemplo, ".xls"). Si no se especifica, el tipo de documento es inaccesible mediante el comando Abrir archivo.

- `CDocTemplate::regFileTypeId`Identificador del tipo de documento que se almacenará en la base de datos de registro mantenida por Windows. Esta cadena es solo para uso interno (por ejemplo, "ExcelWorksheet"). Si no se especifica, el tipo de documento no se puede registrar con el Administrador de archivos de Windows.

- `CDocTemplate::regFileTypeName`Nombre del tipo de documento que se va a almacenar en la base de datos de registro. Esta cadena se puede mostrar en cuadros de diálogo de aplicaciones que tienen acceso a la base de datos de registro (por ejemplo, "Microsoft Excel Worksheet").

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la subcadena especificada; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar una subcadena específica que describa el tipo de documento. La cadena que contiene estas subcadenas se almacena en la plantilla de documento y se deriva de una cadena en el archivo de recursos de la aplicación. El marco de trabajo llama a esta función para obtener las cadenas que necesita para la interfaz de usuario de la aplicación. Si ha especificado una extensión de nombre de archivo para los documentos de la aplicación, el marco de trabajo también llama a esta función al agregar una entrada a la base de datos de registro de Windows; esto permite que los documentos se abran desde el Administrador de archivos de Windows.

Llame a esta función solo si `CDocTemplate`está derivando su propia clase de .

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition

Recupera la posición del primer documento asociado a esta plantilla.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para recorrer en iteración la lista de documentos asociados a esta plantilla de documento; o NULL si la lista está vacía.

### <a name="remarks"></a>Observaciones

Utilice esta función para obtener la posición del primer documento en la lista de documentos asociados a esta plantilla. Utilice el valor POSITION como argumento para [CDocTemplate::GetNextDoc](#getnextdoc) para recorrer en iteración la lista de documentos asociados a la plantilla.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) y [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) invalidan esta función virtual pura. Cualquier clase de `CDocTemplate` la que derive también debe invalidar esta función.

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a>CDocTemplate::GetNextDoc

Recupera el elemento de lista identificado por *rPos*y, a continuación, establece *rPos* en el valor POSITION de la siguiente entrada de la lista.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al siguiente documento de la lista de documentos asociados a esta plantilla.

### <a name="parameters"></a>Parámetros

*Rpos*<br/>
Referencia a un valor POSITION devuelto por una llamada `GetNextDoc`anterior a [GetFirstDocPosition](#getfirstdocposition) o .

### <a name="remarks"></a>Observaciones

Si el elemento recuperado es el último de la lista, el nuevo valor de *rPos* se establece en NULL.

Puede utilizar `GetNextDoc` en un bucle de iteración directa si establece la posición inicial con una llamada a [GetFirstDocPosition](#getfirstdocposition).

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame

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
El documento al que está asociado el marco. Puede ser NULL.

*bMakeVisible*<br/>
Indica si el marco debe ser visible y activo.

### <a name="remarks"></a>Observaciones

Llame `IntitialUpdateFrame` después de `CreateNewFrame`crear un nuevo marco con . Llamar a esta función hace que `OnInitialUpdate` las vistas de esa ventana de marco reciban sus llamadas. Además, si no había anteriormente una vista activa, la vista principal de la ventana de marco se activa; la vista principal es una vista con un identificador secundario de AFX_IDW_PANE_FIRST. Por último, la ventana de marco se hace visible si *bMakeVisible* es distinto de cero. Si *bMakeVisible* es cero, el foco actual y el estado visible de la ventana de marco permanecerán sin cambios.

No es necesario llamar a esta función cuando se utiliza la implementación del marco de trabajo de archivo nuevo y archivo abierto.

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a>CDocTemplate::LoadTemplate

Carga los recursos `CDocTemplate` de una clase determinada o derivada.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para cargar los recursos de una clase determinada `CDocTemplate` o derivada. Normalmente se llama durante la construcción, excepto cuando la plantilla se está construyendo globalmente. En ese caso, `LoadTemplate` la llamada a se retrasa hasta [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) se llama.

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a>CDocTemplate::MatchDocType

Determina el grado de confianza en la coincidencia entre un tipo de documento y esta plantilla.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Nombre de ruta del archivo cuyo tipo se va a determinar.

*rpDocMatch*<br/>
Puntero a un documento al que se asigna el documento coincidente, si el archivo especificado por *lpszPathName* ya está abierto.

### <a name="return-value"></a>Valor devuelto

Valor de la enumeración **Confidence,** que se define de la siguiente manera:

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

Utilice esta función para determinar el tipo de plantilla de documento que se utilizará para abrir un archivo. Si la aplicación admite varios tipos de archivo, por ejemplo, puede usar esta función para `MatchDocType` determinar cuál de las plantillas de documento disponibles es adecuada para un archivo determinado llamando a cada plantilla a su vez y eligiendo una plantilla según el valor de confianza devuelto.

Si el archivo especificado por *lpszPathName* ya `CDocTemplate::yesAlreadyOpen` está abierto, `CDocument` esta función devuelve y copia el objeto del archivo en el objeto en *rpDocMatch*.

Si el archivo no está abierto pero la extensión de *lpszPathName* coincide con la extensión especificada por `CDocTemplate::filterExt`, esta función devuelve `CDocTemplate::yesAttemptNative` y establece *rpDocMatch* en NULL. Para obtener `CDocTemplate::filterExt`más información sobre , vea [CDocTemplate::GetDocString](#getdocstring).

Si ninguno de los casos `CDocTemplate::yesAttemptForeign`es true, la función devuelve .

La implementación predeterminada `CDocTemplate::maybeAttemptForeign` `CDocTemplate::maybeAttemptNative`no devuelve o . Invalide esta función para implementar la lógica de coincidencia de tipos adecuada para la aplicación, quizás utilizando estos dos valores de la enumeración **Confidence.**

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a>CDocTemplate::OpenDocumentFile

Abre un archivo especificado por una ruta de acceso.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
[en] Puntero a la ruta de acceso del archivo que contiene el documento que se va a abrir.

*bAddToMRU*<br/>
[en] TRUE indica que el documento es uno de los archivos más recientes; FALSE indica que el documento no es uno de los archivos más recientes.

### <a name="return-value"></a>Valor devuelto

Puntero al documento cuyo archivo recibe el nombre *lpszPathName*; NULL si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

Abre el archivo cuya ruta de acceso se especifica mediante *lpszPathName*. Si *lpszPathName* es NULL, se crea un nuevo archivo que contiene un documento del tipo asociado a esta plantilla.

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a>CDocTemplate::RemoveDocument

Elimina el documento al que apunta *pDoc* de la lista de documentos asociados a esta plantilla.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Puntero al documento que se va a quitar.

### <a name="remarks"></a>Observaciones

Las clases `CMultiDocTemplate` `CSingleDocTemplate` derivadas y reemplazar esta función. Si deriva su propia clase `CDocTemplate`de plantilla de documento de , la clase derivada debe invalidar esta función.

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a>CDocTemplate::SaveAllModified

Guarda todos los documentos que se han modificado.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario 0.

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a>CDocTemplate::SetContainerInfo

Determina los recursos de los contenedores OLE al editar un elemento OLE en contexto.

```cpp
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parámetros

*nIDOleInPlaceContainer*<br/>
El identificador de los recursos utilizados cuando se activa un objeto incrustado.

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer los recursos que se utilizarán cuando un objeto OLE está activado in situ. Estos recursos pueden incluir menús y tablas de aceleradores. Normalmente se llama a esta función en la función [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de la aplicación.

El menú asociado a *nIDOleInPlaceContainer* contiene separadores que permiten que el menú del elemento en contexto activado se combine con el menú de la aplicación contenedora. Para obtener más información acerca de la combinación de menús de servidor y contenedor, vea el artículo [Menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle

Llame a esta función para cargar el título predeterminado del documento y mostrarlo en la barra de título del documento.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parámetros

*pDocument*<br/>
Puntero al documento cuyo título se va a establecer.

### <a name="remarks"></a>Observaciones

Para obtener información sobre el título `CDocTemplate::docName` predeterminado, vea la descripción de [CDocTemplate::GetDocString](#getdocstring).

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a>CDocTemplate::SetServerInfo

Determina los recursos y las clases cuando el documento del servidor se incrusta o edita in situ.

```cpp
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parámetros

*nIDOleEmbedding*<br/>
El identificador de los recursos utilizados cuando se abre un objeto incrustado en una ventana independiente.

*nIDOleInPlaceServer*<br/>
El identificador de los recursos utilizados cuando un objeto incrustado se activa in situ.

*pOleFrameClass*<br/>
Puntero a una estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que contiene información de clase para el objeto de ventana de marco creado cuando se produce la activación en contexto.

*pOleViewClass*<br/>
Puntero a `CRuntimeClass` una estructura que contiene información de clase para el objeto de vista creado cuando se produce la activación en contexto.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para identificar los recursos que usará la aplicación de servidor cuando el usuario solicita la activación de un objeto incrustado. Estos recursos constan de menús y tablas de aceleradores. Normalmente se llama `InitInstance` a esta función en la aplicación.

El menú asociado a *nIDOleInPlaceServer* contiene separadores que permiten que el menú del servidor se combine con el menú del contenedor. Para obtener más información acerca de la combinación de menús de servidor y contenedor, vea el artículo [Menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame

Crea un marco secundario utilizado para la vista previa enriquecida.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Un puntero a una ventana primaria (normalmente proporcionado por el Shell).

*pDoc*<br/>
Puntero a un objeto de documento, cuyo contenido se previsualizará.

### <a name="return-value"></a>Valor devuelto

Un puntero válido `CFrameWnd` a un objeto, o NULL si se produce un error en la creación.

### <a name="remarks"></a>Observaciones

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo

Configura el controlador de vista previa fuera de proceso.

```cpp
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
Especifica un puntero a una estructura de información de clase en tiempo de ejecución de la vista de vista previa.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate (clase)](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate (clase)](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CScrollView (clase)](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView (clase)](../../mfc/reference/ceditview-class.md)<br/>
[Clase CFormView](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
