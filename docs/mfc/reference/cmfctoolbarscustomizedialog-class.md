---
title: Clase CMFCToolBarsCustomizeDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
ms.openlocfilehash: 4e6bdef10d5747abd344750c888cf6726c47d99e
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929932"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>Clase CMFCToolBarsCustomizeDialog

Cuadro de diálogo no modal de tabulación ( [clase CPropertySheet](../../mfc/reference/cpropertysheet-class.md)) que permite al usuario personalizar las barras de herramientas, menús, métodos abreviados de teclado, herramientas definidas por el usuario y estilo visual de una aplicación. Normalmente, el usuario tiene acceso a este cuadro de diálogo seleccionando **Personalizar** en el menú **Herramientas** .

El cuadro de diálogo **personalizar** tiene seis pestañas: **Comandos**, **barras de herramientas**, **herramientas**, **teclado**, **menú**y **Opciones**.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Construye un objeto `CMFCToolBarsCustomizeDialog`.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)|Inserta un botón de la barra de herramientas en la lista de comandos de la página **comandos** .|
|[CMFCToolBarsCustomizeDialog:: AddMenu](#addmenu)|Carga un menú desde los recursos y llama a [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos de la página **comandos** .|
|[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Carga un menú desde los recursos y llama a [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos de la página **comandos** .|
|[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Carga una barra de herramientas desde los recursos. A continuación, para cada comando del menú, se llama al método [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) para insertar un botón en la lista de comandos de la página **comandos** en la categoría especificada.|
|[CMFCToolBarsCustomizeDialog:: Create](#create)|Muestra el cuadro de diálogo de **Personalización** .|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Reservado para un uso futuro.|
|[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Habilita o deshabilita la creación de nuevas barras de herramientas mediante el cuadro de diálogo **personalizar** .|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Rellena el objeto proporcionado `CListBox` con los comandos de la categoría **todos los comandos** .|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Rellena el objeto proporcionado `CComboBox` con el nombre de cada categoría de comandos en el cuadro de diálogo **personalizar** .|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Rellena el objeto proporcionado `CListBox` con el nombre de cada categoría de comandos en el cuadro de diálogo **personalizar** .|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Recupera el nombre asociado al identificador de comando especificado.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Recupera el número de elementos de la lista proporcionada que tienen una etiqueta de texto determinada.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Recupera el conjunto de marcadores que afectan al comportamiento del cuadro de diálogo.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Inicia un editor de imágenes para que un usuario pueda personalizar un botón de barra de herramientas o un icono de elemento de menú.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Invalida para aumentar la inicialización de la hoja de propiedades. (Invalida [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)).|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Lo llama el marco de trabajo después de que se haya destruido la ventana. (Invalida `CPropertySheet::PostNcDestroy`).|
|[CMFCToolBarsCustomizeDialog:: RemoveButton](#removebutton)|Quita el botón con el identificador de comando especificado de la categoría especificada o de todas las categorías.|
|[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Cambia el nombre de una categoría en el cuadro de lista de categorías en la pestaña **comandos** .|
|[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Reemplaza un botón de la lista de comandos de la pestaña **comandos** por un nuevo objeto de botón de barra de herramientas.|
|[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Agrega una categoría a la lista de categorías que se mostrarán en la pestaña **comandos** .|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Lo llama el marco de trabajo para determinar si la lista de herramientas definidas por el usuario es válida.|
|[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Lo llama el marco de trabajo cuando cambian las propiedades de una herramienta definida por el usuario.|
|[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Determina si un método abreviado de teclado especificado se puede asignar a una acción.|
|[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Determina si se puede cambiar una herramienta definida por el usuario.|
|[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Lo llama el marco de trabajo cuando el usuario elige la pestaña **herramientas** .|

## <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo **personalizar** , cree `CMFCToolBarsCustomizeDialog` un objeto y llame al método [CMFCToolBarsCustomizeDialog:: Create](#create) .

Mientras el cuadro de diálogo **personalizar** está activo, la aplicación funciona en un modo especial que limita al usuario a las tareas de personalización.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarsCustomizeDialog` . En el ejemplo se muestra cómo reemplazar un botón de la barra de herramientas en el cuadro de lista de comandos de la página **comandos** , habilitar la creación de nuevas barras de herramientas mediante el cuadro de diálogo **personalizar** y mostrar el cuadro de diálogo **Personalización** . Este fragmento de código forma parte del [ejemplo de demostración de IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxToolBarsCustomizeDialog. h

##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton

Inserta un botón de la barra de herramientas en la lista de comandos de la página **comandos** .

```
void AddButton(
    UINT uiCategoryId,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);
```

### <a name="parameters"></a>Parámetros

*uiCategoryId*<br/>
de Especifica el identificador de categoría en el que se va a insertar el botón.

*button*<br/>
de Especifica el botón que se va a insertar.

*iInsertBefore*<br/>
de Especifica el índice de base cero de un botón de la barra de herramientas antes de que se inserte el botón.

*lpszCategory*<br/>
de Especifica la cadena de categoría para insertar el botón.

### <a name="remarks"></a>Comentarios

El `AddButton` método omite los botones que tienen los identificadores de comando estándar (como ID_FILE_MRU_FILE1), los comandos que no están permitidos (vea [CMFCToolBar:: IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) y los botones ficticios.

Este método crea un nuevo objeto del mismo tipo que `button` (normalmente una [clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)) mediante el uso de la clase en tiempo de ejecución del botón. Después llama a [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) para copiar los miembros de datos de Button e inserta la copia en la categoría especificada.

Cuando se inserta el botón nuevo, recibe la `OnAddToCustomizePage` notificación.

Si `iInsertBefore` es-1, el botón se anexa a la lista de categorías; de lo contrario, se inserta delante del elemento con el índice especificado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `AddButton` el método de `CMFCToolBarsCustomizeDialog` la clase. Este fragmento de código forma parte del [ejemplo de control deslizante](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu

Carga un menú desde los recursos y llama a [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos de la página **comandos** .

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parámetros

*uiMenuResId*<br/>
de Especifica el identificador de recurso de un menú que se va a cargar.

### <a name="return-value"></a>Valor devuelto

TRUE si se ha agregado un menú correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

En la llamada a `AddMenuCommands`, *bPopup* es false. Como resultado, ese método no agrega elementos de menú que contengan submenús a la lista de comandos. Este método agrega los elementos de menú de los submenús a la lista de comandos.

##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands

Agrega elementos a la lista de comandos de la página **comandos** para representar todos los elementos del menú especificado.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parámetros

*pMenu*<br/>
de Puntero al objeto CMenu que se va a agregar.

*bPopup*<br/>
de Especifica si se van a insertar los elementos de menú emergente en la lista de comandos.

*lpszCategory*<br/>
de Nombre de la categoría en la que se va a insertar el menú.

*lpszMenuPath*<br/>
de Un prefijo que se agrega al nombre cuando el comando se muestra en la lista **todas las categorías** .

### <a name="remarks"></a>Comentarios

El `AddMenuCommands` método recorre todos los elementos de menú de *pMenu*. Para cada elemento de menú que no contiene un submenú, este método crea un objeto de la [clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) y llama al método [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) para agregar el elemento de menú como un botón de la barra de herramientas a la lista de comandos **del Página comandos** . Los separadores se omiten en este proceso.

Si *bPopup* es true, para cada elemento de menú que contenga un submenú, este método crea un objeto de [clase CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) y lo inserta en la lista de `AddButton`comandos mediante una llamada a. De lo contrario, los elementos de menú que contienen submenús no se muestran en la lista de comandos. En cualquier caso, cuando `AddMenuCommands` encuentra un elemento de menú con un submenú, se llama a sí mismo de forma recursiva, pasando un puntero al submenú como el parámetro *pMenu* y anexando la etiqueta del submenú a *lpszMenuPath*.

##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar

Carga una barra de herramientas desde los recursos. A continuación, para cada comando del menú, se llama al método [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) para insertar un botón en la lista de comandos de la página **comandos** en la categoría especificada.

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>Parámetros

*uiCategoryId*<br/>
de Especifica el identificador de recurso de la categoría a la que se va a agregar la barra de herramientas.

*uiToolbarResId*<br/>
de Especifica el identificador de recurso de una barra de herramientas cuyos comandos se insertan en la lista de comandos.

*lpszCategory*<br/>
de Especifica el nombre de la categoría a la que se va a agregar la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

TRUE si el método es correcto; en caso contrario, FALSE.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `AddToolBar` el método en `CMFCToolBarsCustomizeDialog` la clase. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Comentarios

El control que se usa para representar cada comando es un objeto de la [clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) . Después de agregar la barra de herramientas, puede reemplazar el botón por un control de un tipo derivado llamando a [CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton).

##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity

Comprueba la validez de la lista de herramientas de usuario.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parámetros

*lstTools*<br/>
de Lista de herramientas definidas por el usuario que se van a comprobar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la lista de herramientas definidas por el usuario es válida; en caso contrario, FALSE. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método para comprobar la validez de los objetos que representan las herramientas definidas por el usuario devueltas por [CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity).

Invalide el `CheckToolsValidity` método en una clase `CMFCToolBarsCustomizeDialog` derivada de si desea validar las herramientas de usuario antes de que el usuario cierre el cuadro de diálogo. Si este método devuelve FALSE cuando el usuario hace clic en el botón **cerrar** en la esquina superior derecha del cuadro de diálogo o en el botón **cerrar** en la esquina inferior derecha del cuadro de diálogo, el cuadro de diálogo muestra la pestaña **herramientas** en lugar de finales. Si este método devuelve FALSE cuando el usuario hace clic en una pestaña para salir de la pestaña **herramientas** , no se produce la navegación. Debe mostrar un cuadro de mensaje adecuado para informar al usuario del problema que causó un error en la validación.

##  <a name="cmfctoolbarscustomizedialog"></a>  CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

Construye un objeto `CMFCToolBarsCustomizeDialog`.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>Parámetros

*pWndParentFrame*<br/>
de Puntero al marco primario. Este parámetro no debe ser NULL.

*bAutoSetFromMenus*<br/>
de Valor booleano que especifica si se deben agregar los comandos de menú de todos los menús a la lista de comandos de la página **comandos** . Si este parámetro es TRUE, se agregan los comandos de menú. De lo contrario, no se agregan los comandos de menú.

*uiFlags*<br/>
de Combinación de marcas que afectan al comportamiento del cuadro de diálogo. Este parámetro puede ser uno o varios de los siguientes valores:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
de Puntero a una lista de `CRuntimeClass` objetos que especifican páginas personalizadas adicionales.

### <a name="remarks"></a>Comentarios

El parámetro *plistCustomPages* hace referencia a la lista `CRuntimeClass` de objetos que especifican páginas personalizadas adicionales. El constructor agrega más páginas al cuadro de diálogo mediante el método [CRuntimeClass:: CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) . Vea el ejemplo CustomPages para obtener un ejemplo en el que se agregan más páginas al cuadro de diálogo **personalizar** .

Para obtener más información sobre los valores que se pueden pasar en el parámetro *uiFlags* , vea [CMFCToolBarsCustomizeDialog:: GetFlags](#getflags).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de `CMFCToolBarsCustomizeDialog` la clase. Este fragmento de código forma parte del [ejemplo de páginas personalizadas](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create

Muestra el cuadro de diálogo de **Personalización** .

```
virtual BOOL Create();
```

### <a name="return-value"></a>Valor devuelto

TRUE si la hoja de propiedades de personalización se ha creado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame al `Create` método solo después de inicializar por completo la clase.

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Habilita o deshabilita la creación de nuevas barras de herramientas mediante el cuadro de diálogo **personalizar** .

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE para habilitar las barras de herramientas definidas por el usuario; FALSE para deshabilitar las barras de herramientas.

### <a name="remarks"></a>Comentarios

Si *bEnable* es true, los botones **nuevo**, **cambiar nombre** y **eliminar** se muestran en la página **barras de herramientas** .

De forma predeterminada, o si *bEnable* es false, no se muestran estos botones y el usuario no puede definir nuevas barras de herramientas.

##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList

Rellena el objeto proporcionado `CListBox` con los comandos de la categoría **todos los comandos** .

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parámetros

*wndListOfCommands*<br/>
enuncia Referencia al `CListBox` objeto que se va a rellenar.

### <a name="remarks"></a>Comentarios

La categoría **todos los comandos** contiene los comandos de todas las categorías. El método [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) agrega el comando asociado al botón proporcionado a la categoría **todos los comandos** .

Este método borra el contenido del objeto proporcionado `CListBox` antes de rellenarlo con los comandos de la categoría **todos los comandos** .

La `CMFCMousePropertyPage` clase usa este método para rellenar el cuadro de lista de eventos de doble clic.

##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Rellena el objeto proporcionado `CComboBox` con el nombre de cada categoría de comandos en el cuadro de diálogo **personalizar** .

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*wndCategory*<br/>
enuncia Referencia al `CComboBox` objeto que se va a rellenar.

*bAddEmpty*<br/>
de Valor booleano que especifica si se van a agregar categorías al cuadro combinado que no tienen comandos. Si este parámetro es TRUE, las categorías vacías se agregan al cuadro combinado. De lo contrario, no se agregan las categorías vacías.

### <a name="remarks"></a>Comentarios

Este método es como el método [CMFCToolBarsCustomizeDialog:: FillCategoriesListBox](#fillcategorieslistbox) , salvo que este método funciona con `CComboBox` un objeto.

Este método no borra el contenido del `CComboBox` objeto antes de rellenarlo. Garantiza que la categoría **todos los comandos** sea el último elemento del cuadro combinado.

Puede agregar nuevas categorías de comandos mediante el método [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) . Puede cambiar el nombre de una categoría existente mediante el método [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) .

Las `CMFCToolBarsKeyboardPropertyPage` clases `CMFCKeyMapDialog` y utilizan este método para clasificar las asignaciones de teclado.

##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Rellena el objeto proporcionado `CListBox` con el nombre de cada categoría de comandos en el cuadro de diálogo **personalizar** .

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*wndCategory*<br/>
enuncia Referencia al `CListBox` objeto que se va a rellenar.

*bAddEmpty*<br/>
de Valor booleano que especifica si se deben agregar categorías al cuadro de lista que no tengan comandos. Si este parámetro es TRUE, las categorías vacías se agregan al cuadro de lista. De lo contrario, no se agregan las categorías vacías.

### <a name="remarks"></a>Comentarios

Este método es como el método [CMFCToolBarsCustomizeDialog:: FillCategoriesComboBox](#fillcategoriescombobox) , salvo que este método funciona con `CListBox` un objeto.

Este método no borra el contenido del `CListBox` objeto antes de rellenarlo. Garantiza que la categoría **todos los comandos** sea el último elemento en el cuadro de lista.

Puede agregar nuevas categorías de comandos mediante el método [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) . Puede cambiar el nombre de una categoría existente mediante el método [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) .

La `CMFCToolBarsCommandsPropertyPage` clase usa este método para mostrar la lista de comandos que está asociada a cada categoría de comandos.

##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName

Recupera el nombre asociado al identificador de comando especificado.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR del comando que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Nombre asociado al identificador de comando especificado, o NULL si el comando no existe.

##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory

Recupera el número de elementos de la lista proporcionada que tienen una etiqueta de texto determinada.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
de Etiqueta de texto que debe coincidir.

*lstCommands*<br/>
de Referencia a una lista que contiene `CMFCToolBarButton` objetos.

### <a name="return-value"></a>Valor devuelto

Número de elementos de la lista proporcionada cuya etiqueta de texto es igual a *lpszItemName*.

### <a name="remarks"></a>Comentarios

Cada elemento de la lista de objetos proporcionada debe ser de `CMFCToolBarButton`tipo. Este método compara *lpszItemName* con el miembro de datos [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) .

##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags

Recupera el conjunto de marcadores que afectan al comportamiento del cuadro de diálogo.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Valor devuelto

Conjunto de marcas que afectan al comportamiento del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Este método recupera el valor del parámetro *uiFlags* que se pasa al constructor. El valor devuelto puede ser uno o varios de los siguientes valores:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Permite al usuario especificar el aspecto de sombra del menú.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Permite al usuario especificar si se muestran las etiquetas de texto debajo de las imágenes de botón de la barra de herramientas.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Permite al usuario especificar el estilo de animación del menú.  |
|AFX_CUSTOMIZE_NOHELP|Quita el botón ayuda del cuadro de diálogo de personalización.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Habilita el estilo visual WS_EX_CONTEXTHELP.  |
|AFX_CUSTOMIZE_NOTOOLS|Quita la página de **herramientas** del cuadro de diálogo de personalización. Esta marca es válida si la aplicación usa la `CUserToolsManager` clase.  |
|AFX_CUSTOMIZE_MENUAMPERS|Permite que los títulos de los botones contengan el carácter de y comercial ( **&** ).  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Quita la opción **iconos grandes** del cuadro de diálogo Personalización.  |

Para obtener más información sobre el estilo visual WS_EX_CONTEXTHELP, vea [estilos extendidos de ventana](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Responde a un cambio en una herramienta de usuario inmediatamente después de que se produzca.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parámetros

*pSelTool*<br/>
[in, out] Un puntero al objeto de herramienta de usuario que se ha cambiado.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando un usuario cambia las propiedades de una herramienta definida por el usuario. La implementación predeterminada no hace nada. Invalide este método en una clase `CMFCToolBarsCustomizeDialog` derivada de para realizar el procesamiento después de que se produzca un cambio en una herramienta de usuario.

##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey

Valida los métodos abreviados de teclado a medida que un usuario los define.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parámetros

*pAccel*<br/>
[in, out] Puntero al asignación de teclado propuesto que se expresa como una estructura de [aceleración](/windows/win32/api/winuser/ns-winuser-accel) .

### <a name="return-value"></a>Valor devuelto

TRUE si se puede asignar la clave o FALSE si no se puede asignar la clave. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para realizar un procesamiento adicional cuando un usuario asigne un nuevo método abreviado de teclado o para validar los métodos abreviados de teclado cuando el usuario los define. Para evitar que se asigne un acceso directo, devuelva FALSE. También debe mostrar un cuadro de mensaje o, de lo contrario, informar al usuario de la razón por la que se rechazó el método abreviado de teclado.

##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Realiza un procesamiento personalizado cuando se cambia a una herramienta de usuario cuando el usuario está a punto de aplicar un cambio.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parámetros

*pSelTool*<br/>
[in, out] Puntero al objeto de herramienta de usuario que se va a reemplazar.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando las propiedades de una herramienta definida por el usuario están a punto de cambiar. La implementación predeterminada no hace nada. Invalide el método en una clase `CMFCToolBarsCustomizeDialog` derivada de si desea realizar el `OnBeforeChangeTool` procesamiento antes de que se produzca un cambio en una herramienta de usuario, como la liberación de los recursos que usa *pSelTool* .

##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Inicia un editor de imágenes para que un usuario pueda personalizar un botón de barra de herramientas o un icono de elemento de menú.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la ventana primaria.

*bitmap*<br/>
de Referencia a un objeto de mapa de bits que se va a editar.

*nBitsPerPixel*<br/>
de Resolución de color del mapa de bits, en bits por píxel.

### <a name="return-value"></a>Valor devuelto

TRUE si se confirma un cambio; en caso contrario, FALSE. La implementación predeterminada muestra un cuadro de diálogo y devuelve TRUE si el usuario hace clic en **Aceptar**, o false si el usuario hace clic en **Cancelar** o en el botón **cerrar** .

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando el usuario ejecuta el editor de imágenes. La implementación predeterminada muestra el cuadro de diálogo [clase CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md) . Invalide `OnEditToolbarMenuImage` en una clase derivada para usar un editor de imágenes personalizado.

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

Invalida para aumentar la inicialización de la hoja de propiedades.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

El resultado de llamar al método [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) .

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), mostrando el botón **cerrar** , asegurándose de que el cuadro de diálogo se ajusta al tamaño de la pantalla actual y moviendo el botón **ayuda** a la esquina inferior izquierda. del cuadro de diálogo.

##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage

Controla la notificación desde el marco de trabajo que la página de **herramientas** está a punto de inicializarse.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada no hace nada. Invalide este método en una clase derivada para procesar esta notificación.

##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy

Lo llama el marco de trabajo después de que se haya destruido la ventana.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase `CPropertySheet::PostNcDestroy`base,, restaurando la aplicación al modo anterior.

El método [CMFCToolBarsCustomizeDialog:: Create](#create) coloca la aplicación en un modo especial que limita al usuario a las tareas de personalización.

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

Quita el botón con el identificador de comando especificado de la categoría especificada o de todas las categorías.

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>Parámetros

*uiCategoryId*<br/>
de Especifica el identificador de categoría del que se va a quitar el botón.

*uiCmdId*<br/>
de Especifica el identificador de comando del botón.

*lpszCategory*<br/>
de Especifica el nombre de la categoría de la que se va a quitar el botón.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del botón que se ha quitado o-1 si no se ha encontrado el identificador de comando especificado en la categoría especificada. Si *uiCategoryId* es-1, el valor devuelto es 0.

### <a name="remarks"></a>Comentarios

Para quitar un botón de todas las categorías, llame a la primera sobrecarga de este método y establezca *uiCategoryId* en-1.

##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory

Cambia el nombre de una categoría en el cuadro de lista de categorías en la página **comandos** .

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parámetros

*lpszCategoryOld*<br/>
de Nombre de la categoría que se va a cambiar.

*lpszCategoryNew*<br/>
de El nuevo nombre de categoría.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El nombre de la categoría debe ser único.

##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton

Reemplaza un botón de la barra de herramientas en el cuadro de lista de comandos de la página **comandos** .

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de Especifica el comando del botón que se va a reemplazar.

*button*<br/>
de Referencia **const** al objeto de botón de barra de herramientas que reemplaza al botón anterior.

### <a name="remarks"></a>Comentarios

Cuando[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) o [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) agrega un comando a la página **Comandos**, ese comando tiene el formato de un objeto [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) (o un objeto de la clase [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) para un elemento de menú que contiene un submenú agregado por `AddMenuCommands`). El marco también llama a estos tres métodos para agregar comandos automáticamente. Si desea que un comando se represente mediante un tipo derivado, llame `ReplaceButton` a y pase un botón del tipo derivado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `ReplaceButton` el método en `CMFCToolBarsCustomizeDialog` la clase. Este fragmento de código forma parte del [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory

Especifica qué categoría de la lista de categorías de la página **comandos** es la categoría de usuario. Debe llamar a esta función antes de llamar a [CMFCToolBarsCustomizeDialog:: Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parámetros

*lpszCategory*<br/>
de Nombre de la categoría.

### <a name="return-value"></a>Valor devuelto

TRUE si el método es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco de trabajo no utiliza actualmente el valor de la categoría de usuario.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)
