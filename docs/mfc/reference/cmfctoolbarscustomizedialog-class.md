---
title: CMFCToolBarsCustomizeDialog (clase)
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
ms.openlocfilehash: e1dd6fff9fa4f03dbf93510da26c78c73e86c6ab
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780969"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog (clase)

Un cuadro de diálogo no modal de tabulación ( [CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)) que permite al usuario personalizar las barras de herramientas, menús, métodos abreviados de teclado, herramientas definidas por el usuario y el estilo visual de una aplicación. Normalmente, el usuario tiene acceso a este cuadro de diálogo seleccionando **Personalizar** en el menú **Herramientas** .

El **personalizar** cuadro de diálogo tiene seis pestañas: **Comandos**, **las barras de herramientas**, **herramientas**, **teclado**, **menú**, y **opciones**.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Construye un objeto `CMFCToolBarsCustomizeDialog`.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Inserta un botón de barra de herramientas en la lista de comandos en el **comandos** página|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Carga un menú desde los recursos y las llamadas [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos en el **comandos** página.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Carga un menú desde los recursos y las llamadas [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos en el **comandos** página.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Carga una barra de herramientas de los recursos. A continuación, para cada comando en las llamadas de menú el [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método para insertar un botón en la lista de comandos en el **comandos** página bajo la categoría especificada.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|Muestra el **personalización** cuadro de diálogo.|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Reservado para un uso futuro.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Habilita o deshabilita la creación de nuevas barras de herramientas mediante el uso de la **personalizar** cuadro de diálogo.|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Rellena proporcionado `CListBox` objeto con los comandos en el **todos los comandos** categoría.|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Rellena proporcionado `CComboBox` objeto con el nombre de cada categoría de comandos en el **personalizar** cuadro de diálogo.|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Rellena proporcionado `CListBox` objeto con el nombre de cada categoría de comandos en el **personalizar** cuadro de diálogo.|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Recupera el nombre que está asociado con el identificador de comando especificado.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Recupera el número de elementos de la lista proporcionada que tengan una etiqueta de texto determinado.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Recupera el conjunto de indicadores que afectan al comportamiento del cuadro de diálogo.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Inicia un editor de imágenes para que un usuario puede personalizar un icono de elemento de menú o botón de barra de herramientas.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Invalidaciones para aumentar la inicialización de la hoja de propiedades. (Invalida [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Lo llama el marco de trabajo después de que se ha destruido la ventana. (Invalida `CPropertySheet::PostNcDestroy`).|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Quita el botón con el identificador de comando de la categoría especificada, o de todas las categorías.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Cambia el nombre de una categoría en el cuadro de lista de categorías en el **comandos** ficha.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Reemplaza un botón en la lista de comandos en el **comandos** pestaña con un nuevo objeto de botón de barra de herramientas.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Agrega una categoría a la lista de categorías que se mostrará en el **comandos** ficha.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Lo llama el marco de trabajo para determinar si la lista de herramientas definidas por el usuario es válida.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Lo llama el marco cuando cambian las propiedades de una herramienta definido por el usuario.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Determina si un método abreviado especificado puede asignarse a una acción.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Determina si se puede cambiar una herramienta definido por el usuario.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Lo llama el marco cuando el usuario elige el **herramientas** ficha se solicita.|

## <a name="remarks"></a>Comentarios

Para mostrar el **personalizar** diálogo cuadro, cree un `CMFCToolBarsCustomizeDialog` objeto y llamar a la [CMFCToolBarsCustomizeDialog::Create](#create) método.

Mientras el **personalizar** cuadro de diálogo está activo, la aplicación funciona en un modo especial que se limita al usuario a las tareas de personalización.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarsCustomizeDialog` . El ejemplo muestra cómo reemplazar un botón de barra de herramientas en el cuadro de lista de comandos en el **comandos** página, habilite la creación de nuevas barras de herramientas mediante el **personalizar** cuadro de diálogo y mostrar el  **Personalización** cuadro de diálogo. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxToolBarsCustomizeDialog.h

##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton

Inserta un botón de barra de herramientas en la lista de comandos en el **comandos** página.

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
[in] Especifica el identificador de categoría en la que se va a insertar en el botón.

*botón*<br/>
[in] Especifica el botón que se va a insertar.

*iInsertBefore*<br/>
[in] Especifica el índice de base cero de un botón de barra de herramientas antes de que el botón se inserta.

*lpszCategory*<br/>
[in] Especifica la cadena de categoría para insertar el botón.

### <a name="remarks"></a>Comentarios

El `AddButton` método omite los botones que tienen los identificadores de comando estándar (por ejemplo, ID_FILE_MRU_FILE1), que no se permiten los comandos (consulte [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) y los botones de ficticio.

Este método crea un nuevo objeto del mismo tipo como `button` (normalmente un [CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)) mediante el uso de la clase en tiempo de ejecución del botón. A continuación, llama [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) para copiar los miembros de datos del botón e inserta la copia en la categoría especificada.

Cuando se inserta el nuevo botón, recibe el `OnAddToCustomizePage` notificación.

Si `iInsertBefore` es -1, el botón se anexa a la lista de categorías; de lo contrario se inserta delante del elemento con el índice especificado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `AddButton` método de la `CMFCToolBarsCustomizeDialog` clase. Este fragmento de código forma parte de la [ejemplo Slider](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu

Carga un menú desde los recursos y las llamadas [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos en el **comandos** página.

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parámetros

*uiMenuResId*<br/>
[in] Especifica el identificador de recurso de un menú cargar.

### <a name="return-value"></a>Valor devuelto

TRUE si un menú se ha agregado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

En la llamada a `AddMenuCommands`, *bPopup* es FALSE. Como resultado, ese método no agrega elementos de menú que contienen los submenús a la lista de comandos. Este método agrega los elementos de menú en los submenús a la lista de comandos.

##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands

Agrega elementos a la lista de comandos en el **comandos** página para representar todos los elementos en el menú especificado.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parámetros

*pMenu*<br/>
[in] Un puntero al objeto CMenu para agregar.

*bPopup*<br/>
[in] Especifica si se va a insertar los elementos de menú emergente a la lista de comandos.

*lpszCategory*<br/>
[in] El nombre de la categoría que se va a insertar en el menú.

*lpszMenuPath*<br/>
[in] Un prefijo que se agrega al nombre cuando el comando se muestra en el **todas las categorías** lista.

### <a name="remarks"></a>Comentarios

El `AddMenuCommands` método recorre todos los elementos de menú de *pMenu*. Para cada elemento de menú que no tiene un submenú, este método crea un [CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md) objeto y llama a la [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método para agregar el elemento de menú como barra de herramientas botón a la lista de comandos en el **comandos** página. Los separadores se omiten en este proceso.

Si *bPopup* es TRUE, para cada elemento de menú que contiene el submenú de este método crea un [CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md) objeto y lo inserta en la lista de comandos mediante una llamada a `AddButton`. En caso contrario, los elementos de menú que contienen los submenús no se muestran en la lista de comandos. En cualquier caso, cuando `AddMenuCommands` encuentra un elemento de menú con un submenú llama a sí mismo recursivamente, pasando un puntero al submenú como el *pMenu* parámetro y anexar la etiqueta del submenú para *lpszMenuPath*.

##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar

Carga una barra de herramientas de los recursos. A continuación, para cada comando en las llamadas de menú el [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método para insertar un botón en la lista de comandos en el **comandos** página bajo la categoría especificada.

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
[in] Especifica el identificador de recurso de la categoría para agregar la barra de herramientas.

*uiToolbarResId*<br/>
[in] Especifica el identificador de recurso de una barra de herramientas cuyos comandos se insertan en la lista de comandos.

*lpszCategory*<br/>
[in] Especifica el nombre de la categoría que se va a agregar la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realiza correctamente; en caso contrario, FALSE.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `AddToolBar` método en el `CMFCToolBarsCustomizeDialog` clase. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Comentarios

El control que se utiliza para representar cada comando es un [CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md) objeto. Después de agregar la barra de herramientas, puede reemplazar el botón con un control de un tipo derivado mediante una llamada a [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).

##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity

Comprueba la validez de la lista de herramientas de usuario.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parámetros

*lstTools*<br/>
[in] La lista de herramientas definidas por el usuario para comprobar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la lista de herramientas definidas por el usuario es válida; en caso contrario, FALSE. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

El marco llama a este método para comprobar la validez de los objetos que representan las herramientas definidas por el usuario devueltas por [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).

Invalidar el `CheckToolsValidity` método en una clase derivada de `CMFCToolBarsCustomizeDialog` si desea validar las herramientas de usuario antes de que el usuario cierra el cuadro de diálogo. Si este método devuelve FALSE cuando el usuario hace clic en el **cerrar** situado en la esquina superior derecha del cuadro de diálogo o el botón rotulado **cerrar** en la esquina inferior derecha del cuadro de diálogo, el cuadro de diálogo Muestra el **herramientas** pestaña en lugar de cierre. Si este método devuelve FALSE cuando el usuario hace clic en una pestaña que sale de la **herramientas** pestaña, no se produce la navegación. Debe mostrar un cuadro de mensaje adecuado para informar al usuario sobre el problema que provocó el error de validación.

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
[in] Un puntero al marco primario. Este parámetro no debe ser NULL.

*bAutoSetFromMenus*<br/>
[in] Un valor booleano que especifica si se debe agregar los comandos de menú de todos los menús en la lista de comandos en el **comandos** página. Si este parámetro es TRUE, se agregan los comandos de menú. En caso contrario, no se agregan los comandos de menú.

*uiFlags*<br/>
[in] Una combinación de marcas que afectan al comportamiento del cuadro de diálogo. Este parámetro puede ser uno o varios de los siguientes valores:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[in] Un puntero a una lista de `CRuntimeClass` objetos que especifican las páginas personalizadas adicionales.

### <a name="remarks"></a>Comentarios

El *plistCustomPages* parámetro hace referencia a la lista de `CRuntimeClass` objetos que especifican las páginas personalizadas adicionales. El constructor agrega más páginas al cuadro de diálogo mediante el uso de la [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) método. Vea el ejemplo CustomPages para obtener un ejemplo que agrega más páginas para el **personalizar** cuadro de diálogo.

Para obtener más información acerca de los valores que se pueden pasar en el *uiFlags* parámetro, vea [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCToolBarsCustomizeDialog` clase. Este fragmento de código forma parte de la [ejemplo Custom Pages](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create

Muestra el **personalización** cuadro de diálogo.

```
virtual BOOL Create();
```

### <a name="return-value"></a>Valor devuelto

TRUE si la hoja de propiedades de personalización se ha creado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a la `Create` método solo después de inicializar por completo la clase.

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Habilita o deshabilita la creación de nuevas barras de herramientas mediante el uso de la **personalizar** cuadro de diálogo.

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar el*<br/>
[in] TRUE para habilitar las barras de herramientas definidas por el usuario; FALSE para deshabilitar las barras de herramientas.

### <a name="remarks"></a>Comentarios

Si *bHabilitar el* es TRUE, el **New**, **cambiar el nombre de** y **eliminar** botones se mostrarán en el **las barras de herramientas** página.

De forma predeterminada, o si *bHabilitar el* es FALSE, no se muestran estos botones y el usuario no puede definir nuevas barras de herramientas.

##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList

Rellena proporcionado `CListBox` objeto con los comandos en el **todos los comandos** categoría.

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parámetros

*wndListOfCommands*<br/>
[out] Una referencia a la `CListBox` objeto que se va a rellenar.

### <a name="remarks"></a>Comentarios

El **todos los comandos** categoría contiene los comandos de todas las categorías. El [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método agrega el comando que está asociado con el botón proporcionado para el **todos los comandos** categoría por usted.

Este método borra el contenido proporcionado `CListBox` objeto antes de rellenarla con los comandos en el **todos los comandos** categoría.

La `CMFCMousePropertyPage` clase utiliza este método para rellenar el cuadro de lista de eventos de doble clic.

##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Rellena proporcionado `CComboBox` objeto con el nombre de cada categoría de comandos en el **personalizar** cuadro de diálogo.

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*wndCategory*<br/>
[out] Una referencia a la `CComboBox` objeto que se va a rellenar.

*bAddEmpty*<br/>
[in] Un valor booleano que especifica si se debe agregar categorías al cuadro combinado que no tienen comandos. Si este parámetro es TRUE, vacías las categorías se agregan al cuadro combinado. En caso contrario, no se agregan categorías vacías.

### <a name="remarks"></a>Comentarios

Este método es similar a la [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) método salvo que este método funciona con un `CComboBox` objeto.

Este método no borra el contenido de la `CComboBox` objeto antes de rellenarla. Garantiza que el **todos los comandos** categoría es el último elemento en el cuadro combinado.

Puede agregar nuevas categorías de comando mediante el [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método. Puede cambiar el nombre de una categoría existente mediante el [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) método.

El `CMFCToolBarsKeyboardPropertyPage` y `CMFCKeyMapDialog` clases utilizan este método para clasificar las asignaciones de teclado.

##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Rellena proporcionado `CListBox` objeto con el nombre de cada categoría de comandos en el **personalizar** cuadro de diálogo.

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*wndCategory*<br/>
[out] Una referencia a la `CListBox` objeto que se va a rellenar.

*bAddEmpty*<br/>
[in] Un valor booleano que especifica si se debe agregar categorías en el cuadro de lista que no tienen comandos. Si este parámetro es TRUE, vacías las categorías se agregan al cuadro de lista. En caso contrario, no se agregan categorías vacías.

### <a name="remarks"></a>Comentarios

Este método es similar a la [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) método salvo que este método funciona con un `CListBox` objeto.

Este método no borra el contenido de la `CListBox` objeto antes de rellenarla. Garantiza que el **todos los comandos** categoría es el elemento final en el cuadro de lista.

Puede agregar nuevas categorías de comando mediante el [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método. Puede cambiar el nombre de una categoría existente mediante el [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) método.

La `CMFCToolBarsCommandsPropertyPage` clase utiliza este método para mostrar la lista de comandos que está asociada con cada categoría de comandos.

##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName

Recupera el nombre que está asociado con el identificador de comando especificado.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] El identificador del comando que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El nombre que está asociado con el identificador de comando especificado o NULL si no existe el comando.

##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory

Recupera el número de elementos de la lista proporcionada que tengan una etiqueta de texto determinado.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
[in] Para que coincida con la etiqueta de texto.

*lstCommands*<br/>
[in] Una referencia a una lista que contiene `CMFCToolBarButton` objetos.

### <a name="return-value"></a>Valor devuelto

El número de elementos en el lista cuya etiqueta de texto es igual a *lpszItemName*.

### <a name="remarks"></a>Comentarios

Cada elemento en la lista de objetos proporcionado debe ser de tipo `CMFCToolBarButton`. Este método compara *lpszItemName* con el [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) miembro de datos.

##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags

Recupera el conjunto de indicadores que afectan al comportamiento del cuadro de diálogo.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Valor devuelto

El conjunto de indicadores que afectan al comportamiento del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Este método recupera el valor de la *uiFlags* parámetro que se pasa al constructor. El valor devuelto puede ser uno o varios de los siguientes valores:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Permite al usuario especificar la apariencia de la sombra del menú.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Permite al usuario especificar si las etiquetas de texto se muestran debajo de las imágenes de botón de barra de herramientas.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Permite al usuario especificar el estilo de animación de menús.  |
|AFX_CUSTOMIZE_NOHELP|Quita el botón Ayuda en el cuadro de diálogo de personalización.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Permite que el estilo visual WS_EX_CONTEXTHELP.  |
|AFX_CUSTOMIZE_NOTOOLS|Quita el **herramientas** página en el cuadro de diálogo de personalización. Esta marca es válida si la aplicación utiliza la `CUserToolsManager` clase.  |
|AFX_CUSTOMIZE_MENUAMPERS|Permite los títulos de los botones contener la y comercial ( **&**) caracteres.  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Quita el **iconos grandes** opción desde el cuadro de diálogo de personalización.  |

Para obtener más información sobre el estilo visual WS_EX_CONTEXTHELP, consulte [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Responde a un cambio en una herramienta de usuario inmediatamente después de que ocurra.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parámetros

*pSelTool*<br/>
[in, out] Un puntero al objeto de herramienta de usuario que ha cambiado.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando un usuario cambia las propiedades de una herramienta definido por el usuario. La implementación predeterminada no hace nada. Invalide este método en una clase derivada de `CMFCToolBarsCustomizeDialog` para realizar el procesamiento después de que se produce un cambio en una herramienta de usuario.

##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey

Métodos abreviados de teclado se valida como un usuario las define.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parámetros

*pAccel*<br/>
[in, out] Puntero a la asignación de teclado propuesto se expresa como un [aceleración](/windows/desktop/api/winuser/ns-winuser-tagaccel) struct.

### <a name="return-value"></a>Valor devuelto

TRUE si la clave puede ser asignado o FALSE si no se puede asignar la clave. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para realizar un procesamiento adicional cuando un usuario asigna un nuevo método abreviado de teclado, o validar los métodos abreviados de teclado como el usuario los define. Para evitar que un acceso directo que se asigna, devuelve FALSE. Deberá también mostrar un cuadro de mensaje o en caso contrario, informar al usuario sobre el motivo por el que se rechazó el método abreviado de teclado.

##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Realiza el procesamiento personalizado cuando un cambio en una herramienta de usuario cuando el usuario está a punto de aplicar un cambio.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parámetros

*pSelTool*<br/>
[in, out] Un puntero al objeto de herramienta de usuario que se va a reemplazar.

### <a name="remarks"></a>Comentarios

Este método se llama el marco de trabajo cuando las propiedades de una herramienta definido por el usuario que se va a cambiar. La implementación predeterminada no hace nada. Invalidar el `OnBeforeChangeTool` método en una clase derivada de `CMFCToolBarsCustomizeDialog` si desea realizar el procesamiento antes de que se produce un cambio en una herramienta de usuario, como la liberación de recursos que *pSelTool* usa.

##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Inicia un editor de imágenes para que un usuario puede personalizar un icono de elemento de menú o botón de barra de herramientas.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Un puntero a la ventana primaria.

*mapa de bits*<br/>
[in] Una referencia a un objeto de mapa de bits que se va a editar.

*nBitsPerPixel*<br/>
[in] Resolución de color, en bits por píxel del mapa de bits.

### <a name="return-value"></a>Valor devuelto

TRUE si se confirma un cambio; en caso contrario, FALSE. La implementación predeterminada muestra un cuadro de diálogo y devuelve TRUE si el usuario hace clic **Aceptar**, o FALSE si el usuario hace clic **cancelar** o **cerrar** botón.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando el usuario ejecuta el editor de imágenes. La muestra de implementación predeterminado [CMFCImageEditorDialog (clase)](../../mfc/reference/cmfcimageeditordialog-class.md) cuadro de diálogo. Invalidar `OnEditToolbarMenuImage` en una clase derivada para usar un editor de imágenes personalizadas.

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

Invalidaciones para aumentar la inicialización de la hoja de propiedades.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

El resultado de llamar a la [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) método.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), mostrando la **cerrar** botón, asegurándose de que el cuadro de diálogo Ajuste el tamaño de pantalla actual y moviendo el **Ayuda** botón a la esquina inferior izquierda del cuadro de diálogo.

##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage

Controla la notificación desde el marco de trabajo que el **herramientas** página está a punto de inicializarse.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada no hace nada. Invalide este método en una clase derivada para procesar esta notificación.

##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy

Lo llama el marco de trabajo después de que se ha destruido la ventana.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, `CPropertySheet::PostNcDestroy`, mediante la restauración de la aplicación en el modo anterior.

El [CMFCToolBarsCustomizeDialog::Create](#create) método pone la aplicación en un modo especial que se limita al usuario a las tareas de personalización.

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

Quita el botón con el identificador de comando de la categoría especificada, o de todas las categorías.

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
[in] Especifica el identificador de categoría desde la que se va a quitar el botón.

*uiCmdId*<br/>
[in] Especifica el identificador de comando del botón.

*lpszCategory*<br/>
[in] Especifica el nombre de la categoría desde la que se va a quitar el botón.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la botón quitado, o -1 si no se encontró el identificador de comando especificado en la categoría especificada. Si *uiCategoryId* es -1, el valor devuelto es 0.

### <a name="remarks"></a>Comentarios

Para quitar un botón de todas las categorías, llame a la primera sobrecarga de este método y el conjunto *uiCategoryId* en -1.

##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory

Cambia el nombre de una categoría en el cuadro de lista de categorías en el **comandos** página.

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parámetros

*lpszCategoryOld*<br/>
[in] Para cambiar el nombre de categoría.

*lpszCategoryNew*<br/>
[in] El nuevo nombre de categoría.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El nombre de categoría debe ser único.

##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton

Reemplaza un botón de barra de herramientas en el cuadro de lista de comandos en el **comandos** página.

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] Especifica el comando del botón que se debe reemplazar.

*botón*<br/>
[in] Un **const** referencia al objeto de botón de barra de herramientas que reemplaza al botón anterior.

### <a name="remarks"></a>Comentarios

Cuando [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), o [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) agrega una comando para el **comandos** página, que el comando está en forma de un [CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md) objeto (o un [CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md) objeto para un menú elemento que contiene un submenú agregado por `AddMenuCommands`). El marco de trabajo también llama a estos tres métodos para agregar comandos automáticamente. Si desea una línea de comandos para representarlo mediante un tipo derivado en su lugar, llame a `ReplaceButton` y pase un botón del tipo derivado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `ReplaceButton` método en el `CMFCToolBarsCustomizeDialog` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory

Especifica qué categoría en la lista de categorías en el **comandos** página es la categoría de usuario. Debe llamar a esta función antes de llamar a [CMFCToolBarsCustomizeDialog::Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parámetros

*lpszCategory*<br/>
[in] El nombre de la categoría.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El valor de la categoría de usuario no se usa actualmente por el marco de trabajo.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)
