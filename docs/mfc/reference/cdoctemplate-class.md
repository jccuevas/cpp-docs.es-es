---
title: CDocTemplate (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 243881a2ca18ba54e3a6c9cafee407f07746baca
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336990"
---
# <a name="cdoctemplate-class"></a>CDocTemplate (clase)
Una clase base abstracta que define la funcionalidad básica para las plantillas de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Construye un objeto `CDocTemplate`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocTemplate::AddDocument](#adddocument)|Agrega un documento a una plantilla.|  
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Cierra todos los documentos asociados con esta plantilla.|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Crea un nuevo documento.|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|Crea una nueva ventana de marco que contiene un documento y vista.|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|Crea una ventana de marco OLE habilitados.|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Crea un marco secundario que se usa para la vista previa avanzada.|  
|[CDocTemplate::GetDocString](#getdocstring)|Recupera una cadena asociada con el tipo de documento.|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Recupera la posición del primer documento asociado a esta plantilla.|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|Recupera un documento y la posición del siguiente.|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicializa la ventana de marco y, opcionalmente, que es visible.|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|Carga los recursos para un determinado `CDocTemplate` o clase derivada.|  
|[CDocTemplate::MatchDocType](#matchdoctype)|Determina el grado de confianza en la coincidencia entre un tipo de documento y esta plantilla.|  
|[CDocTemplate:: OpenDocumentFile](#opendocumentfile)|Se abre un archivo especificado por una ruta de acceso.|  
|[CDocTemplate::RemoveDocument](#removedocument)|Quita un documento de una plantilla.|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|Guarda todos los documentos asociados con esta plantilla que se han modificado.|  
|[CDocTemplate:: SetContainerInfo](#setcontainerinfo)|Determina los recursos de contenedores OLE al editar un elemento OLE en contexto.|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Muestra el título predeterminado en la barra de título de la ventana de documento.|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Controlador de vista previa de las instalaciones fuera del proceso.|  
|[CDocTemplate:: SetServerInfo](#setserverinfo)|Determina los recursos y las clases cuando el documento de servidor se incrusta o edita en contexto.|  
  
## <a name="remarks"></a>Comentarios  
 Suele crear una o varias plantillas de documento en la implementación de la aplicación `InitInstance` función. Una plantilla de documento define las relaciones entre los tres tipos de clases:  
  
-   Una clase de documento, que deriva de `CDocument`.  
  
-   Una clase de vista, que muestra los datos de la clase de documento mencionada anteriormente. Puede derivar esta clase desde `CView`, `CScrollView`, `CFormView`, o `CEditView`. (También puede usar `CEditView` directamente.)  
  
-   Una clase de ventana de marco, que contiene la vista. Para una aplicación de único documento (SDI) de la interfaz, se deriva esta clase de `CFrameWnd`. Para una aplicación de múltiples documentos (MDI) de la interfaz, se deriva esta clase de `CMDIChildWnd`. Si no tiene que personalizar el comportamiento de la ventana de marco, puede usar `CFrameWnd` o `CMDIChildWnd` directamente sin tener que derivar su propia clase.  
  
 La aplicación tiene una plantilla de documento para cada tipo de documento que admite. Por ejemplo, si la aplicación es compatible con hojas de cálculo y documentos de texto, la aplicación tiene dos objetos de plantilla de documento. Cada plantilla de documento es responsable de crear y administrar todos los documentos de su tipo.  
  
 La plantilla de documento almacena punteros a la `CRuntimeClass` objetos para el documento y vista de clases de ventana de marco. Estos `CRuntimeClass` objetos se especifican al crear una plantilla de documento.  
  
 La plantilla de documento contiene el identificador de los recursos utilizados con el tipo de documento (por ejemplo, los recursos de la tabla de aceleradores, icono o menú). La plantilla de documento también tiene las cadenas que contienen información adicional acerca de su tipo de documento. Estos incluyen el nombre del tipo de documento (por ejemplo, "hoja") y la extensión de archivo (por ejemplo, ".xls"). Si lo desea, puede contener otras cadenas usadas la interfaz de usuario de la aplicación, el Administrador de archivos de Windows y Object Linking y compatibilidad con la incrustación de objetos (OLE).  
  
 Si la aplicación es un contenedor OLE o del servidor, la plantilla de documento también define el identificador del menú usado durante la activación en contexto. Si la aplicación es un servidor OLE, la plantilla de documento define el identificador de la barra de herramientas y menús que se utiliza durante la activación en contexto. Especificar estos recursos adicionales de OLE mediante una llamada a `SetContainerInfo` y `SetServerInfo`.  
  
 Dado que `CDocTemplate` es una clase abstracta, no puede utilizar la clase directamente. Una aplicación típica usa uno de los dos `CDocTemplate`-derivados de las clases proporcionadas por la biblioteca Microsoft Foundation Class: `CSingleDocTemplate`, que implementa SDI, y `CMultiDocTemplate`, que implementa MDI. Vea las clases para obtener más información sobre el uso de plantillas de documento.  
  
 Si la aplicación requiere un paradigma de interfaz de usuario que es fundamentalmente diferente de SDI o MDI, puede derivar su propia clase de `CDocTemplate`.  
  
 Para obtener más información sobre `CDocTemplate`, consulte [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="adddocument"></a>  CDocTemplate::AddDocument  
 Utilice esta función para agregar un documento a una plantilla.  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDoc*  
 Un puntero al documento que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) y [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) reemplazar esta función. Si derivar su propia clase de plantilla de documento de `CDocTemplate`, la clase derivada debe reemplazar esta función.  
  
##  <a name="cdoctemplate"></a>  CDocTemplate::CDocTemplate  
 Construye un objeto `CDocTemplate`.  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDResource*  
 Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir recursos de cadena, icono, tabla de aceleradores y menús.  
  
 El recurso de cadena consta de hasta siete subcadenas separadas por el carácter '\n' (el carácter '\n' es necesario como un marcador de posición si no se incluye una subcadena; sin embargo, no son necesarios los caracteres finales '\n'); Estos subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, consulte [GetDocString](#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Tenga en cuenta que la cadena comienza con un carácter '\n'; Esto es porque la primera subcadena no se utiliza para las aplicaciones MDI y por lo tanto, no se incluye. Puede editar esta cadena utilizando el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadena, no como siete entradas independientes.  
  
 *pDocClass*  
 Apunta a la `CRuntimeClass` objeto de la clase de documento. Esta clase es un `CDocument`-derivado de la clase que defina para representar los documentos.  
  
 *pFrameClass*  
 Apunta a la `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede ser un `CFrameWnd`-clase derivada, o puede ser `CFrameWnd` Sí si desea el comportamiento predeterminado de la ventana de marco principal.  
  
 *pViewClass*  
 Apunta a la `CRuntimeClass` objeto de la clase de vista. Esta clase es un `CView`-derivado de la clase que defina para mostrar los documentos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro para construir un `CDocTemplate` objeto. Asignar dinámicamente un `CDocTemplate` objeto y pasarlo a [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) desde el `InitInstance` función miembro de la clase de aplicación.  
  
##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments  
 Llame a esta función miembro para cerrar todos los documentos abiertos.  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEndSession*  
 No usado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se utiliza normalmente como parte del comando archivo salir. La implementación predeterminada de esta función llama a la [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) función miembro para eliminar datos del documento y, a continuación, cierre las ventanas de marco para todas las vistas asociadas al documento.  
  
 Reemplace esta función si desea exigir al usuario realizar limpiezas especiales antes de cerrar el documento de procesamiento. Por ejemplo, si el documento representa un registro en una base de datos, es posible que desee reemplazar esta función para cerrar la base de datos.  
  
##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument  
 Llame a esta función miembro para crear un nuevo documento del tipo asociado a esta plantilla de documento.  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento recién creado, o NULL si se produce un error.  
  
##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame  
 Crea una nueva ventana de marco que contiene un documento y vista.  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDoc*  
 El documento al que debe consultar la nueva ventana de marco. Puede ser NULL.  
  
 *pOther*  
 La ventana de marco en el que la nueva ventana de marco es que basarse. Puede ser NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana de marco recién creada, o NULL si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 `CreateNewFrame` usa el `CRuntimeClass` objetos pasan al constructor para crear una nueva ventana de marco con una vista y el documento adjunto. Si el *pDoc* parámetro es NULL, el marco de trabajo genera un mensaje de seguimiento.  
  
 El *pOther* parámetro se usa para implementar el comando nueva ventana. Proporciona una ventana de marco en el que se va a la nueva ventana de marco de modelo. La nueva ventana de marco normalmente se crea invisible. Llame a esta función para crear ventanas de marco fuera de la implementación de marco estándar de archivo nuevo y abrir archivo.  
  
##  <a name="createoleframe"></a>  CDocTemplate::CreateOleFrame  
 Crea una ventana de marco OLE.  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>Parámetros  
 *pParentWnd*  
 Un puntero a la ventana del marco primario.  
  
 *pDoc*  
 Un puntero al documento al que debe consultar la nueva ventana de marco OLE.  
  
 *bCreateView*  
 Determina si se crea una vista, junto con el marco.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una ventana de marco si se realiza correctamente; en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
 Si *bCreateView* es cero, se crea un marco vacío.  
  
##  <a name="getdocstring"></a>  CDocTemplate::GetDocString  
 Recupera una cadena asociada con el tipo de documento.  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *rString*  
 Una referencia a un `CString` objeto que va a contener la cadena de resultado que devuelve la función.  
  
 *index*  
 Un índice de la subcadena que se va a recuperar de la cadena que describe el tipo de documento. Este parámetro puede tener uno de los valores siguientes:  
  
- `CDocTemplate::windowTitle` Nombre que aparece en (por ejemplo, "Microsoft Excel") de la barra de título de la ventana de la aplicación. Presente solo en la plantilla de documento para las aplicaciones SDI.  
  
- `CDocTemplate::docName` Raíz para el nombre del documento predeterminado (por ejemplo, "Hoja"). Esta raíz, más un número, se utiliza para el nombre predeterminado de un nuevo documento de este tipo siempre que el usuario selecciona el comando nuevo en el menú archivo (por ejemplo, "Hoja1" o "Sheet2"). Si no se especifica, se usa "Sin título" como el valor predeterminado.  
  
- `CDocTemplate::fileNewName` Nombre de este tipo de documento. Si la aplicación admite más de un tipo de documento, esta cadena se muestra en el cuadro de diálogo nuevo archivo (por ejemplo, "hoja"). Si no se especifica, el tipo de documento es accesible mediante el comando nuevo archivo.  
  
- `CDocTemplate::filterName` Descripción del tipo de documento y un carácter comodín filtrar documentos coincidentes de este tipo. Esta cadena se muestra en la lista de archivos de tipo de lista desplegable en el cuadro de diálogo Abrir archivo (por ejemplo, "hojas de cálculo (*.xls)"). Si no se especifica, el tipo de documento es accesible mediante el comando Abrir archivo.  
  
- `CDocTemplate::filterExt` Extensión de documentos de este tipo (por ejemplo, ".xls"). Si no se especifica, el tipo de documento es accesible mediante el comando Abrir archivo.  
  
- `CDocTemplate::regFileTypeId` Identificador para el tipo de documento que se almacenará en la base de datos de registro mantenida por Windows. Esta cadena es solo para uso interno (por ejemplo, "ExcelWorksheet"). Si no se especifica, el tipo de documento no se puede registrar con el Administrador de archivos de Windows.  
  
- `CDocTemplate::regFileTypeName` Nombre del tipo de documento que se almacenará en la base de datos de registro. Esta cadena puede mostrarse en los cuadros de diálogo de las aplicaciones que tienen acceso a la base de datos de registro (por ejemplo, "hoja de Microsoft Excel").  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se encontró la subcadena especificada; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar una subcadena concreta que describe el tipo de documento. Cadena que contiene estos subcadenas se almacena en la plantilla de documento y se deriva de una cadena en el archivo de recursos para la aplicación. El marco de trabajo llama a esta función para obtener las cadenas que necesita para la interfaz de usuario de la aplicación. Si ha especificado una extensión de nombre de archivo para los documentos de la aplicación, el marco de trabajo también llama a esta función cuando se agrega una entrada a la base de datos de registro de Windows; Esto permite que los documentos que se puede abrir desde el Administrador de archivos de Windows.  
  
 Llame a esta función solo si va a derivar su propia clase de `CDocTemplate`.  
  
##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition  
 Recupera la posición del primer documento asociado a esta plantilla.  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de posición que puede utilizarse para recorrer en iteración la lista de documentos asociados con esta plantilla de documento; o NULL si la lista está vacía.  
  
### <a name="remarks"></a>Comentarios  
 Use esta función para obtener la posición del primer documento en la lista de documentos asociados con esta plantilla. Utilice el valor de posición como un argumento a [CDocTemplate::GetNextDoc](#getnextdoc) para recorrer en iteración la lista de documentos asociados con la plantilla.  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) y [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) invalidar esta función virtual pura. Cualquier clase que deriva de `CDocTemplate` también debe reemplazar esta función.  
  
##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc  
 Recupera el elemento de lista identificado por *RPO*, a continuación, establece *RPO* en el valor de posición de la siguiente entrada en la lista.  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al siguiente documento en la lista de documentos asociados con esta plantilla.  
  
### <a name="parameters"></a>Parámetros  
 *RPO*  
 Una referencia a un valor de posición devuelto por una llamada anterior a [GetFirstDocPosition](#getfirstdocposition) o `GetNextDoc`.  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento recuperado es el último en la lista, a continuación, el nuevo valor de *RPO* se establece en NULL.  
  
 Puede usar `GetNextDoc` en un bucle de iteración de avance, si establece la posición inicial con una llamada a [GetFirstDocPosition](#getfirstdocposition).  
  
 Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame  
 Inicializa la ventana de marco y, opcionalmente, que es visible.  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pFrame*  
 La ventana de marco que necesita la actualización inicial.  
  
 *pDoc*  
 El documento al que está asociado el marco. Puede ser NULL.  
  
 *bMakeVisible*  
 Indica si el marco estarán visibles y activas.  
  
### <a name="remarks"></a>Comentarios  
 Llame a `IntitialUpdateFrame` después de crear un nuevo marco con `CreateNewFrame`. Llamar a esta función hace que las vistas en esa ventana de marco para recibir sus `OnInitialUpdate` llamadas. Además, si anteriormente no era una vista activa, la vista principal de la ventana de marco se pondrá en activa; la vista primaria es una vista con un elemento secundario Id. de AFX_IDW_PANE_FIRST. Por último, la ventana de marco se hace visible si *bMakeVisible* es distinto de cero. Si *bMakeVisible* es cero, el foco actual y el estado de visibilidad de la ventana de marco permanecerá sin cambios.  
  
 No es necesario llamar a esta función cuando se usa la implementación del marco de trabajo de archivo nuevo y abrir archivo.  
  
##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate  
 Carga los recursos para un determinado `CDocTemplate` o clase derivada.  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para cargar los recursos para un determinado `CDocTemplate` o clase derivada. Normalmente se llama durante la construcción, excepto cuando se construye la plantilla global. En ese caso, la llamada a `LoadTemplate` se retrasa hasta [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) se llama.  
  
##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType  
 Determina el grado de confianza en la coincidencia entre un tipo de documento y esta plantilla.  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszPathName*  
 Nombre de ruta del archivo cuyo tipo se va a determinar.  
  
 *rpDocMatch*  
 Puntero a un documento que se asigna el documento coincidente, si el archivo especificado por *lpszPathName* ya está abierto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de la **confianza** enumeración, que se define como sigue:  
  
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
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para determinar el tipo de plantilla de documento que se utilizará para abrir un archivo. Si la aplicación admite varios tipos de archivo, por ejemplo, puede usar esta función para determinar cuál de las plantillas de documento disponibles es adecuada para un archivo determinado mediante una llamada a `MatchDocType` para cada plantilla en el turno y elegir una plantilla de acuerdo con Devuelve el valor de confianza.  
  
 Si el archivo especificado por *lpszPathName* ya está abierta, esta función devuelve `CDocTemplate::yesAlreadyOpen` y copia el archivo `CDocument` objeto en el objeto en *rpDocMatch*.  
  
 Si el archivo no está abierto, pero la extensión en *lpszPathName* coincide con la extensión especificada por `CDocTemplate::filterExt`, esta función devuelve `CDocTemplate::yesAttemptNative` y establece *rpDocMatch* en NULL. Para obtener más información sobre `CDocTemplate::filterExt`, consulte [CDocTemplate::GetDocString](#getdocstring).  
  
 Si ningún caso es true, la función devuelve `CDocTemplate::yesAttemptForeign`.  
  
 La implementación predeterminada devuelve `CDocTemplate::maybeAttemptForeign` o `CDocTemplate::maybeAttemptNative`. Reemplace esta función para implementar la lógica de coincidencia de tipo apropiado para su aplicación, quizá con estos dos valores de la **confianza** enumeración.  
  
##  <a name="opendocumentfile"></a>  CDocTemplate:: OpenDocumentFile  
 Se abre un archivo especificado por una ruta de acceso.  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszPathName*  
 Puntero a la ruta de acceso del archivo que contiene el documento que se va a abrirse.  
  
 [in] *bAddToMRU*  
 TRUE indica que el documento es uno de los archivos más recientes; FALSE indica que el documento no es uno de los archivos más recientes.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento cuyo archivo se denomina por *lpszPathName*; Es NULL si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Abre el archivo cuya ruta de acceso especificado por *lpszPathName*. Si *lpszPathName* es NULL, se crea un nuevo archivo que contiene un documento del tipo asociado a esta plantilla.  
  
##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument  
 Quita el documento al que apunta *pDoc* en la lista de documentos asociados con esta plantilla.  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDoc*  
 Puntero al documento que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas `CMultiDocTemplate` y `CSingleDocTemplate` reemplazar esta función. Si derivar su propia clase de plantilla de documento de `CDocTemplate`, la clase derivada debe reemplazar esta función.  
  
##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified  
 Guarda todos los documentos que se han modificado.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se realiza correctamente; en caso contrario, es 0.  
  
##  <a name="setcontainerinfo"></a>  CDocTemplate:: SetContainerInfo  
 Determina los recursos de contenedores OLE al editar un elemento OLE en contexto.  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDOleInPlaceContainer*  
 El identificador de los recursos utilizados cuando se activa un objeto incrustado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para definir los recursos que se usará cuando un objeto OLE está activado en contexto. Estos recursos pueden incluir los menús y las tablas de aceleradores. Esta función normalmente se llama el [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) función de la aplicación.  
  
 El menú asociado *nIDOleInPlaceContainer* contiene separadores que permiten el menú del elemento activado en contexto para combinar con el menú de la aplicación contenedora. Para obtener más información acerca de cómo combinar los menús de servidor y un contenedor, consulte el artículo [menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle  
 Llame a esta función para cargar el título del documento predeterminado y lo muestra en la barra de título del documento.  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pDocument*  
 Puntero al documento cuyo título que se va a establecer.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información sobre el título predeterminado, vea la descripción de `CDocTemplate::docName` en [CDocTemplate::GetDocString](#getdocstring).  
  
##  <a name="setserverinfo"></a>  CDocTemplate:: SetServerInfo  
 Determina los recursos y las clases cuando el documento de servidor se incrusta o edita en contexto.  
  
```  
void SetServerInfo(
    UINT nIDOleEmbedding,  
    UINT nIDOleInPlaceServer = 0,  
    CRuntimeClass* pOleFrameClass = NULL,  
    CRuntimeClass* pOleViewClass = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDOleEmbedding*  
 El identificador de los recursos utilizados cuando se abre un objeto incrustado en una ventana independiente.  
  
 *nIDOleInPlaceServer*  
 El identificador de los recursos usados cuando un objeto incrustado es activa en contexto.  
  
 *pOleFrameClass*  
 Puntero a un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que contiene información de la clase del objeto de ventana de marco creado cuando se produce la activación en contexto.  
  
 *pOleViewClass*  
 Puntero a un `CRuntimeClass` estructura que contiene información de clase para el objeto de vista que se crean cuando se produce la activación en contexto.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para identificar los recursos que se usará en la aplicación de servidor cuando el usuario solicita la activación de un objeto incrustado. Estos recursos consisten en los menús y las tablas de aceleradores. Esta función normalmente se llama el `InitInstance` de la aplicación.  
  
 El menú asociado *nIDOleInPlaceServer* contiene separadores que permiten el menú de servidor para combinar con el menú del contenedor. Para obtener más información acerca de cómo combinar los menús de servidor y un contenedor, consulte el artículo [menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame  
 Crea un marco secundario que se usa para la vista previa avanzada.  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parámetros  
 *pParentWnd*  
 Un puntero a una ventana primaria (normalmente proporcionada por el Shell).  
  
 *pDoc*  
 Un puntero a un objeto de documento cuyo contenido se mostrará una vista previa.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a un `CFrameWnd` de objeto, o NULL si se produce un error en la creación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo  
 Configura el fuera de controlador de vista previa de proceso.  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDPreviewFrame*  
 Especifica un identificador de recurso del marco de vista previa.  
  
 *pPreviewFrameClass*  
 Especifica un puntero a una estructura de información de clase en tiempo de ejecución del marco de vista previa.  
  
 *pPreviewViewClass*  
 Especifica un puntero a una estructura de información de clase en tiempo de ejecución de la vista previa.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate (clase)](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate (clase)](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CScrollView (clase)](../../mfc/reference/cscrollview-class.md)   
 [CEditView (clase)](../../mfc/reference/ceditview-class.md)   
 [CFormView (clase)](../../mfc/reference/cformview-class.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
