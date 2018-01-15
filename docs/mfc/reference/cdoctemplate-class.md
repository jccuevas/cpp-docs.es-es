---
title: CDocTemplate (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71d44aac1ca7a018be7be1b375dd92920af96dba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Cierra todos los documentos asociados a esta plantilla.|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Crea un nuevo documento.|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|Crea una nueva ventana de marco que contiene un documento y la vista.|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|Crea una ventana de marco OLE habilitados.|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Crea un marco de secundario usado para la vista previa avanzada.|  
|[CDocTemplate::GetDocString](#getdocstring)|Recupera una cadena asociada con el tipo de documento.|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Recupera la posición del primer documento asociado a esta plantilla.|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|Recupera un documento y la posición de la siguiente.|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicializa la ventana de marco y, opcionalmente, lo hace visible.|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|Carga los recursos de un determinado `CDocTemplate` o clase derivada.|  
|[CDocTemplate::MatchDocType](#matchdoctype)|Determina el grado de confianza de la coincidencia entre un tipo de documento y esta plantilla.|  
|[CDocTemplate:: OpenDocumentFile](#opendocumentfile)|Abre un archivo especificado por una ruta de acceso.|  
|[CDocTemplate::RemoveDocument](#removedocument)|Quita un documento de una plantilla.|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|Guarda todos los documentos asociados a esta plantilla que se han modificado.|  
|[CDocTemplate:: SetContainerInfo](#setcontainerinfo)|Determina los recursos de contenedores OLE al editar un elemento OLE en contexto.|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Muestra el título predeterminado en la barra de título de la ventana de documento.|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Controlador de vista previa de configuraciones fuera del proceso.|  
|[CDocTemplate:: SetServerInfo](#setserverinfo)|Determina los recursos y las clases cuando el documento de servidor se incrusta o edita en contexto.|  
  
## <a name="remarks"></a>Comentarios  
 Se suele crean una o varias plantillas de documento en la implementación de la aplicación `InitInstance` (función). Una plantilla de documento define las relaciones entre los tres tipos de clases:  
  
-   Una clase de documento, que derivan de **CDocument**.  
  
-   Una clase de vista, que muestra los datos de la clase de documento mencionado anteriormente. Puede derivar de esta clase desde `CView`, `CScrollView`, `CFormView`, o `CEditView`. (También puede usar `CEditView` directamente.)  
  
-   Una clase de ventana de marco, que contiene la vista. Para una aplicación de único documento (SDI) de la interfaz, se deriva esta clase de `CFrameWnd`. Para una aplicación de múltiples documentos (MDI) de la interfaz, se deriva esta clase de `CMDIChildWnd`. Si no es necesario personalizar el comportamiento de la ventana de marco, puede usar `CFrameWnd` o `CMDIChildWnd` directamente sin tener que derivar su propia clase.  
  
 La aplicación tiene una plantilla de documento para cada tipo de documento que admite. Por ejemplo, si la aplicación es compatible con las hojas de cálculo y documentos de texto, la aplicación tiene dos objetos de plantilla de documento. Cada plantilla de documento es responsable de crear y administrar todos los documentos de su tipo.  
  
 La plantilla de documento almacena punteros a la `CRuntimeClass` objetos de documento, vista y las clases de ventana de marco. Estos `CRuntimeClass` objetos se especifican al crear una plantilla de documento.  
  
 La plantilla de documento contiene el identificador de los recursos utilizados con el tipo de documento (por ejemplo, menú, icono o recursos de la tabla de aceleradores). La plantilla de documento también tiene las cadenas que contienen información adicional acerca de su tipo de documento. Estos incluyen el nombre del tipo de documento (por ejemplo, "hoja") y la extensión de archivo (por ejemplo, ".xls"). Si lo desea, puede contener otra cadena usada por la interfaz de usuario de la aplicación, el Administrador de archivos de Windows y vincular el objeto y compatibilidad con la incrustación de objetos (OLE).  
  
 Si la aplicación es un contenedor OLE o del servidor, la plantilla de documento también define el identificador del menú que se utiliza durante la activación en contexto. Si la aplicación es un servidor OLE, la plantilla de documento define el identificador de la barra de herramientas y el menú que se utiliza durante la activación en contexto. Especificar estos recursos adicionales de OLE mediante una llamada a `SetContainerInfo` y `SetServerInfo`.  
  
 Dado que `CDocTemplate` es una clase abstracta, no se puede utilizar la clase directamente. Una aplicación típica utiliza uno de los dos `CDocTemplate`-derivadas de las clases proporcionadas por la biblioteca Microsoft Foundation Class: `CSingleDocTemplate`, que implementa SDI, y `CMultiDocTemplate`, que implementa MDI. Consulte esas clases para obtener más información sobre el uso de plantillas de documento.  
  
 Si la aplicación requiere un paradigma de interfaz de usuario que es diferente de SDI o MDI, puede derivar su propia clase de `CDocTemplate`.  
  
 Para obtener más información sobre `CDocTemplate`, consulte [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="adddocument"></a>CDocTemplate::AddDocument  
 Utilice esta función para agregar un documento a una plantilla.  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDoc`  
 Un puntero al documento que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) y [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) invalidan esta función. Si derivar su propia clase de plantilla de documento de `CDocTemplate`, la clase derivada debe reemplazar esta función.  
  
##  <a name="cdoctemplate"></a>CDocTemplate::CDocTemplate  
 Construye un objeto `CDocTemplate`.  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDResource`  
 Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir menú, icono, tabla de aceleradores y recursos de cadena.  
  
 El recurso de cadena consta de hasta siete subcadenas separados por el carácter '\n' (se necesita el carácter '\n' como marcador de posición si no se incluye una subcadena; sin embargo, no son necesarios los caracteres finales '\n'); Estos subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, consulte [GetDocString](#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Tenga en cuenta que la cadena comienza con un carácter '\n'; Esto es porque la primera subcadena no se utiliza para las aplicaciones MDI y por lo tanto, no se incluye. Puede editar esta cadena mediante el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadena, no como siete separe las entradas.  
  
 `pDocClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de documento. Esta clase es un **CDocument**-deriva la clase que defina para representar los documentos.  
  
 `pFrameClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede ser un `CFrameWnd`-clase derivada, o puede ser `CFrameWnd` si desea el comportamiento predeterminado de la ventana de marco principal.  
  
 `pViewClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de vista. Esta clase es un `CView`-deriva la clase que defina para mostrar los documentos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro para construir un `CDocTemplate` objeto. Asignar dinámicamente un `CDocTemplate` objeto y pasarlo a [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) desde el `InitInstance` función miembro de la clase de aplicación.  
  
##  <a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments  
 Llame a esta función miembro para cerrar todos los documentos abiertos.  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEndSession`  
 Especifica si no se finaliza la sesión. Es **TRUE** si se va a la sesión finaliza; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se utiliza normalmente como parte del comando salida de archivo. La implementación predeterminada de esta función llama el [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) función de miembro para eliminar datos del documento y, a continuación, cierre las ventanas de marco para todas las vistas que se adjuntan al documento.  
  
 Reemplace esta función si desea exigir al usuario que realice la operación de limpieza especial de procesamiento antes de cerrar el documento. Por ejemplo, si el documento representa un registro de una base de datos, puede que desee anular esta función para cerrar la base de datos.  
  
##  <a name="createnewdocument"></a>CDocTemplate::CreateNewDocument  
 Llame a esta función miembro para crear un nuevo documento del tipo asociado a esta plantilla de documento.  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento recién creado, o **NULL** si se produce un error.  
  
##  <a name="createnewframe"></a>CDocTemplate::CreateNewFrame  
 Crea una nueva ventana de marco que contiene un documento y la vista.  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDoc`  
 El documento a la que debe hacer referencia la nueva ventana de marco. Puede ser **NULL**.  
  
 `pOther`  
 La ventana de marco en el que es basará la nueva ventana de marco. Puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana de marco recién creada, o **NULL** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 `CreateNewFrame`usa el `CRuntimeClass` objetos pasan al constructor para crear una nueva ventana de marco con una vista y el documento adjunto. Si el `pDoc` parámetro es **NULL**, el marco de trabajo genera un mensaje de seguimiento.  
  
 El `pOther` parámetro se utiliza para implementar el comando nueva ventana. Proporciona una ventana de marco en el que se va a modelar la nueva ventana de marco. La nueva ventana de marco normalmente se crea sea invisible. Llame a esta función para crear ventanas de marco fuera de la implementación estándar de framework de archivo nuevo y abrir archivo.  
  
##  <a name="createoleframe"></a>CDocTemplate::CreateOleFrame  
 Crea una ventana de marco OLE.  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Un puntero a la ventana del marco principal.  
  
 `pDoc`  
 Un puntero al documento en el que debe hacer referencia la nueva ventana de marco OLE.  
  
 `bCreateView`  
 Determina si se crea una vista junto con el marco.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una ventana de marco si se realiza correctamente; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si `bCreateView` es cero, se crea un marco vacío.  
  
##  <a name="getdocstring"></a>CDocTemplate::GetDocString  
 Recupera una cadena asociada con el tipo de documento.  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rString`  
 Una referencia a un `CString` objeto que va a contener la cadena cuando la función devuelve.  
  
 *índice*  
 Un índice de la subcadena que se va a recuperar de la cadena que describe el tipo de documento. Este parámetro puede tener uno de los valores siguientes:  
  
- **CDocTemplate::windowTitle** nombre que aparece en el título de la ventana de la aplicación de la barra (por ejemplo, "Microsoft Excel"). Presentar solo en la plantilla de documento para aplicaciones SDI.  
  
- **CDocTemplate::docName** raíz para el nombre de documento predeterminado (por ejemplo, "Hoja"). Esta raíz, más un número, se utiliza para el nombre predeterminado de un nuevo documento de este tipo siempre que el usuario selecciona el comando nuevo en el menú archivo (por ejemplo, "Sheet1" o "Sheet2"). Si no se especifica, se utiliza "Sin título" como el valor predeterminado.  
  
- **FileNewName** nombre de este tipo de documento. Si la aplicación admite más de un tipo de documento, esta cadena se muestra en el cuadro de diálogo nuevo archivo (por ejemplo, "hoja"). Si no se especifica, el tipo de documento es accesible mediante el comando archivo nuevo.  
  
- **CDocTemplate::filterName** descripción del tipo de documento y un filtro comodín documentos de este tipo de búsqueda de coincidencias. Esta cadena se muestra en la lista de archivos de tipo de lista desplegable en el cuadro de diálogo Abrir archivo (por ejemplo, "hojas de cálculo (*.xls)"). Si no se especifica, el tipo de documento es accesible mediante el comando Abrir archivo.  
  
- **CDocTemplate::filterExt** extensión para los documentos de este tipo (por ejemplo, ".xls"). Si no se especifica, el tipo de documento es accesible mediante el comando Abrir archivo.  
  
- **CDocTemplate::regFileTypeId** identificador para el tipo de documento que se almacenará en la base de datos del Registro mantenida por Windows. Esta cadena es sólo para uso interno (por ejemplo, "ExcelWorksheet"). Si no se especifica, el tipo de documento no se puede registrar con el Administrador de archivos de Windows.  
  
- **CDocTemplate::regFileTypeName** nombre del tipo de documento que se almacenará en la base de datos de registro. Esta cadena puede mostrarse en los cuadros de diálogo de las aplicaciones que tienen acceso a la base de datos de registro (por ejemplo, "hoja de Microsoft Excel").  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encontró la subcadena especificada; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar una subcadena concreta que describe el tipo de documento. Cadena que contiene estos subcadenas se almacena en la plantilla de documento y se deriva de una cadena en el archivo de recursos para la aplicación. El marco de trabajo llama a esta función para obtener las cadenas que necesita para la interfaz de usuario de la aplicación. Si ha especificado una extensión de nombre de archivo para los documentos de su aplicación, el marco de trabajo también llama a esta función cuando se agrega una entrada a la base de datos de registro de Windows; Esto permite que los documentos que se abran desde el Administrador de archivos de Windows.  
  
 Llame a esta función solo si va a derivar su propia clase de `CDocTemplate`.  
  
##  <a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition  
 Recupera la posición del primer documento asociado a esta plantilla.  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que puede usarse para recorrer en iteración la lista de documentos asociados a esta plantilla de documento; o **NULL** si la lista está vacía.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para obtener la posición del primer documento en la lista de documentos asociados con esta plantilla. Use la **posición** valor como argumento a [CDocTemplate::GetNextDoc](#getnextdoc) para recorrer en iteración la lista de documentos asociados a la plantilla.  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) y [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) invalidar esta función virtual pura. Cualquier clase que derive de `CDocTemplate` también debe reemplazar esta función.  
  
##  <a name="getnextdoc"></a>CDocTemplate::GetNextDoc  
 Recupera el elemento de lista identificado por `rPos`, a continuación, establece `rPos` a la **posición** valor de la entrada siguiente en la lista.  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al siguiente documento en la lista de documentos asociados con esta plantilla.  
  
### <a name="parameters"></a>Parámetros  
 `rPos`  
 Una referencia a un **posición** valor devuelto por una llamada anterior a [GetFirstDocPosition](#getfirstdocposition) o `GetNextDoc`.  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento recuperado es el último en la lista, a continuación, el nuevo valor de `rPos` está establecido en **NULL**.  
  
 Puede usar `GetNextDoc` en un bucle de iteración de avance, si establece la posición inicial con una llamada a [GetFirstDocPosition](#getfirstdocposition).  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
##  <a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame  
 Inicializa la ventana de marco y, opcionalmente, lo hace visible.  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFrame`  
 La ventana de marco que necesita la actualización inicial.  
  
 `pDoc`  
 El documento al que está asociado el marco. Puede ser **NULL**.  
  
 `bMakeVisible`  
 Indica si el marco debería estar visibles y activas.  
  
### <a name="remarks"></a>Comentarios  
 Llame a **IntitialUpdateFrame** después de crear un nuevo marco con `CreateNewFrame`. Llamar a esta función hace que las vistas en la ventana de marco para recibir sus `OnInitialUpdate` llamadas. Además, si anteriormente no era una vista activa, la vista de la ventana de marco principal estará activa; la vista principal es una vista con un identificador secundario de **AFX_IDW_PANE_FIRST**. Por último, la ventana de marco se hace visible si `bMakeVisible` es distinto de cero. Si `bMakeVisible` es cero, el foco actual y el estado de visibilidad de la ventana de marco permanecerán sin cambios.  
  
 No es necesario llamar a esta función cuando se usa la implementación del marco de trabajo de archivo nuevo y abrir archivo.  
  
##  <a name="loadtemplate"></a>CDocTemplate::LoadTemplate  
 Carga los recursos de un determinado `CDocTemplate` o clase derivada.  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para cargar los recursos de un determinado `CDocTemplate` o clase derivada. Normalmente se llama durante la construcción, excepto cuando la plantilla se está construyendo globalmente. En ese caso, la llamada a `LoadTemplate` se retrasa hasta el [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) se llama.  
  
##  <a name="matchdoctype"></a>CDocTemplate::MatchDocType  
 Determina el grado de confianza de la coincidencia entre un tipo de documento y esta plantilla.  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Ruta de acceso del archivo cuyo tipo se va a determinar.  
  
 `rpDocMatch`  
 Puntero a un documento que se asigna el documento coincidente, si el archivo especificado por `lpszPathName` ya está abierto.  
  
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
 Utilice esta función para determinar el tipo de plantilla de documento que se utilizará para abrir un archivo. Si la aplicación admite varios tipos de archivo, por ejemplo, puede usar esta función para determinar cuál de las plantillas de documento disponible es adecuado para un archivo determinado mediante una llamada a `MatchDocType` para cada plantilla de y elegir una plantilla de acuerdo con Devuelve el valor de confianza.  
  
 Si el archivo especificado por `lpszPathName` ya está abierto, esta función devuelve **CDocTemplate::yesAlreadyOpen** y copia el archivo **CDocument** objeto en el objeto en `rpDocMatch`.  
  
 Si el archivo no está abierto pero la extensión en `lpszPathName` coincide con la extensión especificada por **CDocTemplate::filterExt**, esta función devuelve **CDocTemplate::yesAttemptNative** y establece `rpDocMatch` a **NULL**. Para obtener más información sobre **CDocTemplate::filterExt**, consulte [CDocTemplate::GetDocString](#getdocstring).  
  
 Si ningún caso es true, la función devuelve **CDocTemplate::yesAttemptForeign**.  
  
 La implementación predeterminada no devuelve **CDocTemplate::maybeAttemptForeign** o **CDocTemplate::maybeAttemptNative**. Reemplace esta función para implementar la lógica de coincidencia de tipos adecuado para su aplicación, posiblemente utilizando estos dos valores de la **confianza** enumeración.  
  
##  <a name="opendocumentfile"></a>CDocTemplate:: OpenDocumentFile  
 Abre un archivo especificado por una ruta de acceso.  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszPathName`  
 Puntero a la ruta de acceso del archivo que contiene el documento que se va a abrir.  
  
 [in] `bAddToMRU`  
 `TRUE`indica que el documento es uno de los archivos más recientes; `FALSE` indica que el documento no es uno de los archivos más recientes.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento cuyo archivo se denomina por `lpszPathName`; `NULL` si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Abre el archivo cuya ruta de acceso se especifica por `lpszPathName`. Si `lpszPathName` es `NULL`, se crea un nuevo archivo que contiene un documento del tipo asociado a esta plantilla.  
  
##  <a name="removedocument"></a>CDocTemplate::RemoveDocument  
 Quita el documento que señala `pDoc` en la lista de documentos asociados con esta plantilla.  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDoc`  
 Puntero al documento que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas `CMultiDocTemplate` y `CSingleDocTemplate` invalidan esta función. Si derivar su propia clase de plantilla de documento de `CDocTemplate`, la clase derivada debe reemplazar esta función.  
  
##  <a name="saveallmodified"></a>CDocTemplate::SaveAllModified  
 Guarda todos los documentos que se han modificado.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente; en caso contrario es 0.  
  
##  <a name="setcontainerinfo"></a>CDocTemplate:: SetContainerInfo  
 Determina los recursos de contenedores OLE al editar un elemento OLE en contexto.  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDOleInPlaceContainer`  
 El identificador de los recursos que usa cuando se activa un objeto incrustado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para definir los recursos que se utilizará cuando un objeto OLE esté activado en el contexto. Estos recursos pueden incluir los menús y tablas de aceleradores. Esta función se suele llamar el [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) función de la aplicación.  
  
 El menú asociado `nIDOleInPlaceContainer` contiene separadores que permiten el menú del elemento activado en contexto para combinar con el menú de la aplicación contenedora. Para obtener más información acerca de cómo combinar los menús de servidor y un contenedor, consulte el artículo [menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle  
 Llame a esta función para cargar el título del documento predeterminado y mostrarlo en la barra de título del documento.  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pDocument*  
 Puntero al documento cuyo título que se va a establecer.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información sobre el título predeterminado, vea la descripción de **CDocTemplate::docName** en [CDocTemplate::GetDocString](#getdocstring).  
  
##  <a name="setserverinfo"></a>CDocTemplate:: SetServerInfo  
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
 El identificador de los recursos que usa cuando se abre un objeto incrustado en una ventana independiente.  
  
 `nIDOleInPlaceServer`  
 El identificador de los recursos que usa cuando un objeto incrustado está activado en contexto.  
  
 *pOleFrameClass*  
 Puntero a un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que contiene información de clase para el objeto de ventana de marco creado cuando se produce la activación en contexto.  
  
 *pOleViewClass*  
 Puntero a un `CRuntimeClass` estructura que contiene información de clase para el objeto de vista que se crea cuando se produce la activación en contexto.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para identificar los recursos que se utilizarán en la aplicación de servidor cuando el usuario solicita la activación de un objeto incrustado. Estos recursos consisten en los menús y tablas de aceleradores. Esta función se suele llamar el `InitInstance` de la aplicación.  
  
 El menú asociado `nIDOleInPlaceServer` contiene separadores que permiten el menú del servidor combinar con el menú del contenedor. Para obtener más información acerca de cómo combinar los menús de servidor y un contenedor, consulte el artículo [menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame  
 Crea un marco de secundario usado para la vista previa avanzada.  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Un puntero a una ventana primaria (normalmente proporcionada por el Shell).  
  
 `pDoc`  
 Un puntero a un objeto de documento, se mostrará una vista previa cuyo contenido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a una `CFrameWnd` objeto, o `NULL` si se produce un error en la creación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo  
 Configura el fuera de controlador de vista previa de proceso.  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDPreviewFrame`  
 Especifica un identificador de recursos del marco de vista previa.  
  
 `pPreviewFrameClass`  
 Especifica un puntero a una estructura de información de clase en tiempo de ejecución del marco de vista previa.  
  
 `pPreviewViewClass`  
 Especifica un puntero a una estructura de información de clase en tiempo de ejecución de la vista previa.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)   
 [Clase CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CScrollView (clase)](../../mfc/reference/cscrollview-class.md)   
 [Clase CEditView](../../mfc/reference/ceditview-class.md)   
 [Clase CFormView](../../mfc/reference/cformview-class.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)
