---
title: CMFCToolBarsCustomizeDialog (Clase)
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
ms.openlocfilehash: d47ecf45a7bbfc563be0c05cd15ee84d430f502f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377361"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog (Clase)

Un cuadro de diálogo de ficha no basado en el usuario ( [CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)que permite al usuario personalizar las barras de herramientas, los menús, los métodos abreviados de teclado, las herramientas definidas por el usuario y el estilo visual en una aplicación. Normalmente, el usuario tiene acceso a este cuadro de diálogo seleccionando **Personalizar** en el menú **Herramientas** .

El cuadro de diálogo **Personalizar** tiene seis pestañas: **Comandos**, **Barras de herramientas**, **Herramientas**, **Teclado**, **Menú**y **Opciones**.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Construye un objeto `CMFCToolBarsCustomizeDialog`.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Inserta un botón de barra de herramientas en la lista de comandos de la página **Comandos**|
|[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Carga un menú desde los recursos y llama a [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos de la página **Comandos.**|
|[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Carga un menú desde los recursos y llama a [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos de la página **Comandos.**|
|[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Carga una barra de herramientas desde los recursos. A continuación, para cada comando del menú llama al método [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) para insertar un botón en la lista de comandos de la página **Comandos** de la categoría especificada.|
|[CMFCToolBarsCustomizeDialog::Crear](#create)|Muestra el cuadro de diálogo **Personalización.**|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Reservado para uso futuro.|
|[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Habilita o deshabilita la creación de nuevas barras de herramientas mediante el cuadro de diálogo **Personalizar.**|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Rellena el `CListBox` objeto proporcionado con los comandos de la categoría **Todos los comandos.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Rellena el `CComboBox` objeto proporcionado con el nombre de cada categoría de comando en el cuadro de diálogo **Personalizar.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Rellena el `CListBox` objeto proporcionado con el nombre de cada categoría de comando en el cuadro de diálogo **Personalizar.**|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Recupera el nombre asociado al identificador de comando especificado.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Recupera el número de elementos de la lista proporcionada que tienen una etiqueta de texto determinada.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Recupera el conjunto de indicadores que afectan al comportamiento del cuadro de diálogo.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Inicia un editor de imágenes para que un usuario pueda personalizar un botón de barra de herramientas o un icono de elemento de menú.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Reemplazaciones para aumentar la inicialización de la hoja de propiedades. (Reemplaza [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Llamado por el marco de trabajo después de que la ventana se ha destruido. (Invalida `CPropertySheet::PostNcDestroy`).|
|[CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Quita el botón con el identificador de comando especificado de la categoría especificada o de todas las categorías.|
|[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Cambia el nombre de una categoría en el cuadro de lista de categorías de la ficha **Comandos.**|
|[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Reemplaza un botón de la lista de comandos de la ficha **Comandos** por un nuevo objeto de botón de barra de herramientas.|
|[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Agrega una categoría a la lista de categorías que se mostrarán en la pestaña **Comandos.**|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Llamado por el marco de trabajo para determinar si la lista de herramientas definidas por el usuario es válida.|
|[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Llamado por el marco de trabajo cuando cambian las propiedades de una herramienta definida por el usuario.|
|[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Determina si se puede asignar un método abreviado de teclado especificado a una acción.|
|[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Determina si se puede cambiar una herramienta definida por el usuario.|
|[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Llamado por el marco de trabajo cuando el usuario elige la pestaña **Herramientas** se solicita.|

## <a name="remarks"></a>Observaciones

Para mostrar el cuadro de `CMFCToolBarsCustomizeDialog` diálogo **Personalizar,** cree un objeto y llame al método [CMFCToolBarsCustomizeDialog::Create.](#create)

Mientras el cuadro de diálogo **Personalizar** está activo, la aplicación funciona en un modo especial que limita al usuario a las tareas de personalización.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarsCustomizeDialog` . En el ejemplo se muestra cómo reemplazar un botón de barra de herramientas en el cuadro de lista de comandos de la página **Comandos,** habilitar la creación de nuevas barras de herramientas mediante el cuadro de diálogo **Personalizar** y mostrar el cuadro de diálogo **Personalización.** Este fragmento de código forma parte del ejemplo de demostración de [IE.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxToolBarsCustomizeDialog.h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton

Inserta un botón de barra de herramientas en la lista de comandos de la página **Comandos.**

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
[en] Especifica el identificador de categoría en el que se va a insertar el botón.

*Botón*<br/>
[en] Especifica el botón que se va a insertar.

*iInsertBefore*<br/>
[en] Especifica el índice de base cero de un botón de barra de herramientas antes del cual se inserta el botón.

*lpszCategory*<br/>
[en] Especifica la cadena de categoría para insertar el botón.

### <a name="remarks"></a>Observaciones

El `AddButton` método omite los botones que tienen los ideos de comando estándar (como ID_FILE_MRU_FILE1), comandos que no están permitidos (consulte [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) y botones ficticios.

Este método crea un nuevo objeto `button` del mismo tipo que (normalmente un [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md)) mediante la clase en tiempo de ejecución del botón. A continuación, llama a [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) para copiar los miembros de datos de button e inserta la copia en la categoría especificada.

Cuando se inserta el nuevo botón, recibe la `OnAddToCustomizePage` notificación.

Si `iInsertBefore` es -1, el botón se anexa a la lista de categorías; de lo contrario, se inserta antes del elemento con el índice especificado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `AddButton` muestra `CMFCToolBarsCustomizeDialog` cómo utilizar el método de la clase. Este fragmento de código forma parte del [ejemplo Slider.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CMFCToolBarsCustomizeDialog::AddMenu

Carga un menú desde los recursos y llama a [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) para agregar ese menú a la lista de comandos de la página **Comandos.**

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parámetros

*uiMenuResId*<br/>
[en] Especifica el identificador de recurso de un menú que se va a cargar.

### <a name="return-value"></a>Valor devuelto

TRUESi un menú se ha agregado correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

En la `AddMenuCommands`llamada a , *bPopup* es FALSE. Como resultado, ese método no agrega elementos de menú que contienen submenús a la lista de comandos. Este método agrega los elementos de menú de los submenús a la lista de comandos.

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands

Agrega elementos a la lista de comandos de la página **Comandos** para representar todos los elementos del menú especificado.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parámetros

*pMenu*<br/>
[en] Un puntero a la CMenu objeto que se va a agregar.

*bPopup*<br/>
[en] Especifica si se deben insertar los elementos del menú emergente en la lista de comandos.

*lpszCategory*<br/>
[en] El nombre de la categoría para insertar el menú.

*lpszMenuPath*<br/>
[en] Prefijo que se agrega al nombre cuando el comando se muestra en la lista **Todas las categorías.**

### <a name="remarks"></a>Observaciones

El `AddMenuCommands` método recorre todos los elementos de menú de *pMenu*. Para cada elemento de menú que no contiene un submenú, este método crea un [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objeto y llama a la [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método para agregar el elemento de menú como un botón de barra de herramientas a la lista de comandos en el **comandos** página. Los separadores se omiten en este proceso.

Si *bPopup* es TRUE, para cada elemento de menú que contiene un submenú, este método crea un `AddButton`objeto [CMFCToolBarMenuButton (Clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md) y lo inserta en la lista de comandos llamando a . De lo contrario, los elementos de menú que contienen submenús no se muestran en la lista de comandos. En cualquier caso, cuando `AddMenuCommands` encuentra un elemento de menú con un submenú se llama a sí mismo recursivamente, pasando un puntero al submenú como el *pMenu* parámetro y anexando la etiqueta del submenú a *lpszMenuPath*.

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar

Carga una barra de herramientas desde los recursos. A continuación, para cada comando del menú llama al método [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) para insertar un botón en la lista de comandos de la página **Comandos** de la categoría especificada.

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
[en] Especifica el identificador de recurso de la categoría a la que se va a agregar la barra de herramientas.

*uiToolbarResId*<br/>
[en] Especifica el identificador de recurso de una barra de herramientas cuyos comandos se insertan en la lista de comandos.

*lpszCategory*<br/>
[en] Especifica el nombre de la categoría a la que se va a agregar la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; de lo contrario FALSO.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `AddToolBar` muestra `CMFCToolBarsCustomizeDialog` cómo utilizar el método en la clase. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Observaciones

El control que se utiliza para representar cada comando es un [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objeto. Después de agregar la barra de herramientas, puede reemplazar el botón con un control de un tipo derivado llamando a [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity

Comprueba la validez de la lista de herramientas de usuario.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parámetros

*lstTools*<br/>
[en] La lista de herramientas definidas por el usuario que se deben comprobar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la lista de herramientas definidas por el usuario es válida; de lo contrario FALSO. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método para comprobar la validez de los objetos que representan las herramientas definidas por el usuario devueltas por [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).

Invalide `CheckToolsValidity` el método en `CMFCToolBarsCustomizeDialog` una clase derivada de si desea validar las herramientas de usuario antes de que el usuario cierre el cuadro de diálogo. Si este método devuelve FALSE cuando el usuario hace clic en el botón **Cerrar** en la esquina superior derecha del cuadro de diálogo o en el botón denominado **Cerrar** en la esquina inferior derecha del cuadro de diálogo, el cuadro de diálogo muestra la pestaña **Herramientas** en lugar de cerrar. Si este método devuelve FALSE cuando el usuario hace clic en una pestaña para navegar fuera de la pestaña **Herramientas,** no se produce la navegación. Debe mostrar un cuadro de mensaje adecuado para informar al usuario del problema que provocó un error en la validación.

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

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
[en] Un puntero al marco primario. Este parámetro no debe ser NULL.

*bAutoSetFromMenus*<br/>
[en] Valor booleano que especifica si se deben agregar los comandos de menú de todos los menús a la lista de comandos de la página **Comandos.** Si este parámetro es TRUE, se agregan los comandos de menú. De lo contrario, no se agregan los comandos de menú.

*uiFlags*<br/>
[en] Combinación de indicadores que afectan al comportamiento del cuadro de diálogo. Este parámetro puede ser uno o varios de los siguientes valores:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[en] Puntero a una `CRuntimeClass` lista de objetos que especifican páginas personalizadas adicionales.

### <a name="remarks"></a>Observaciones

El parámetro *plistCustomPages* hace `CRuntimeClass` referencia a la lista de objetos que especifican páginas personalizadas adicionales. El constructor agrega más páginas al cuadro de diálogo mediante el [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) método. Consulte el CustomPages ejemplo para obtener un ejemplo que agrega más páginas al **personalizar** cuadro de diálogo.

Para obtener más información acerca de los valores que puede pasar en el parámetro *uiFlags,* vea [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCToolBarsCustomizeDialog` cómo construir un objeto de la clase. Este fragmento de código forma parte del [ejemplo Páginas personalizadas.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CMFCToolBarsCustomizeDialog::Crear

Muestra el cuadro de diálogo **Personalización.**

```
virtual BOOL Create();
```

### <a name="return-value"></a>Valor devuelto

TRUESi la hoja de propiedades de personalización se crea correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame `Create` al método solo después de inicializar completamente la clase.

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Habilita o deshabilita la creación de nuevas barras de herramientas mediante el cuadro de diálogo **Personalizar.**

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para habilitar las barras de herramientas definidas por el usuario; FALSE para deshabilitar las barras de herramientas.

### <a name="remarks"></a>Observaciones

Si *bHabilitar* es TRUE, los botones **Nuevo**, **Cambiar nombre** y **Eliminar** se muestran en la página **Barras de** herramientas.

De forma predeterminada, o si *bEnable* es FALSE, estos botones no se muestran y el usuario no puede definir nuevas barras de herramientas.

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList

Rellena el `CListBox` objeto proporcionado con los comandos de la categoría **Todos los comandos.**

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parámetros

*wndListOfCommands*<br/>
[fuera] Una referencia `CListBox` al objeto que se va a rellenar.

### <a name="remarks"></a>Observaciones

La categoría **Todos los comandos** contiene los comandos de todas las categorías. El [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método agrega el comando que está asociado con el botón proporcionado a la **Todos los comandos** categoría para usted.

Este método borra el contenido `CListBox` del objeto proporcionado antes de rellenarlo con los comandos de la categoría **Todos los comandos.**

La `CMFCMousePropertyPage` clase utiliza este método para rellenar el cuadro de lista de eventos de doble clic.

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Rellena el `CComboBox` objeto proporcionado con el nombre de cada categoría de comando en el cuadro de diálogo **Personalizar.**

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*wndCategory*<br/>
[fuera] Una referencia `CComboBox` al objeto que se va a rellenar.

*bAddEmpty*<br/>
[en] Valor booleano que especifica si se deben agregar categorías al cuadro combinado que no tienen comandos. Si este parámetro es TRUE, se agregan categorías vacías al cuadro combinado. De lo contrario, no se agregan categorías vacías.

### <a name="remarks"></a>Observaciones

Este método es como el [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) método `CComboBox` excepto que este método funciona con un objeto.

Este método no borra el `CComboBox` contenido del objeto antes de rellenarlo. Garantiza que la categoría **Todos los comandos** es el elemento final del cuadro combinado.

Puede agregar nuevas categorías de comandos mediante el [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método. Puede cambiar el nombre de una categoría existente mediante el [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) método.

Las `CMFCToolBarsKeyboardPropertyPage` `CMFCKeyMapDialog` clases y usan este método para categorizar las asignaciones de teclado.

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Rellena el `CListBox` objeto proporcionado con el nombre de cada categoría de comando en el cuadro de diálogo **Personalizar.**

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*wndCategory*<br/>
[fuera] Una referencia `CListBox` al objeto que se va a rellenar.

*bAddEmpty*<br/>
[en] Valor booleano que especifica si se deben agregar categorías al cuadro de lista que no tienen comandos. Si este parámetro es TRUE, se agregan categorías vacías al cuadro de lista. De lo contrario, no se agregan categorías vacías.

### <a name="remarks"></a>Observaciones

Este método es como el [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) método `CListBox` excepto que este método funciona con un objeto.

Este método no borra el `CListBox` contenido del objeto antes de rellenarlo. Garantiza que la categoría **Todos los comandos** es el elemento final del cuadro de lista.

Puede agregar nuevas categorías de comandos mediante el [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) método. Puede cambiar el nombre de una categoría existente mediante el [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) método.

La `CMFCToolBarsCommandsPropertyPage` clase utiliza este método para mostrar la lista de comandos asociados a cada categoría de comandos.

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CMFCToolBarsCustomizeDialog::GetCommandName

Recupera el nombre asociado al identificador de comando especificado.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El ID del comando que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El nombre que está asociado con el identificador de comando especificado, o NULL si el comando no existe.

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory

Recupera el número de elementos de la lista proporcionada que tienen una etiqueta de texto determinada.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parámetros

*lpszItemName*<br/>
[en] La etiqueta de texto que se debe hacer coincidir.

*lstCommands*<br/>
[en] Una referencia a una `CMFCToolBarButton` lista que contiene objetos.

### <a name="return-value"></a>Valor devuelto

El número de elementos de la lista proporcionada cuya etiqueta de texto es igual *a lpszItemName*.

### <a name="remarks"></a>Observaciones

Cada elemento de la lista de `CMFCToolBarButton`objetos proporcionado debe ser de tipo . Este método compara *lpszItemName* con el [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) miembro de datos.

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags

Recupera el conjunto de indicadores que afectan al comportamiento del cuadro de diálogo.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Valor devuelto

Conjunto de indicadores que afectan al comportamiento del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Este método recupera el valor del parámetro *uiFlags* que se pasa al constructor. El valor devuelto puede ser uno o varios de los siguientes valores:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Permite al usuario especificar la apariencia de sombra del menú.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Permite al usuario especificar si las etiquetas de texto se muestran debajo de las imágenes del botón de la barra de herramientas.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Permite al usuario especificar el estilo de animación de menú.  |
|AFX_CUSTOMIZE_NOHELP|Quita el botón de ayuda del cuadro de diálogo de personalización.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Habilita el estilo visual WS_EX_CONTEXTHELP.  |
|AFX_CUSTOMIZE_NOTOOLS|Quita la página **Herramientas** del cuadro de diálogo de personalización. Esta marca es válida si `CUserToolsManager` la aplicación utiliza la clase.  |
|AFX_CUSTOMIZE_MENUAMPERS|Permite que los subtítulos de **&** botón contengan el carácter ampersand ( ).  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Quita la opción **Iconos grandes** del cuadro de diálogo de personalización.  |

Para obtener más información sobre el estilo visual WS_EX_CONTEXTHELP, vea Estilos de [ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Responde a un cambio en una herramienta de usuario inmediatamente después de que se produce.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parámetros

*pSelTool*<br/>
[adentro, fuera] Puntero al objeto de herramienta de usuario que se ha cambiado.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando un usuario cambia las propiedades de una herramienta definida por el usuario. La implementación predeterminada no hace nada. Invalide este método en `CMFCToolBarsCustomizeDialog` una clase derivada de realizar el procesamiento después de que se produzca un cambio en una herramienta de usuario.

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey

Valida los métodos abreviados de teclado como un usuario los define.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parámetros

*pAccel*<br/>
[adentro, fuera] Puntero al assigment de teclado propuesto que se expresa como una estructura [ACCEL.](/windows/win32/api/winuser/ns-winuser-accel)

### <a name="return-value"></a>Valor devuelto

TRUESi se puede asignar la clave o FALSE si no se puede asignar la clave. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada para realizar un procesamiento adicional cuando un usuario asigna un nuevo método abreviado de teclado o para validar los métodos abreviados de teclado como el usuario los define. Para evitar que se asigne un acceso directo, devuelva FALSE. También debe mostrar un cuadro de mensaje o informar al usuario de la razón por la que se rechazó el método abreviado de teclado.

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Realiza el procesamiento personalizado cuando un cambio en una herramienta de usuario cuando el usuario está a punto de aplicar un cambio.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parámetros

*pSelTool*<br/>
[adentro, fuera] Puntero al objeto de herramienta de usuario que está a punto de reemplazarse.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando las propiedades de una herramienta definida por el usuario está a punto de cambiar. La implementación predeterminada no hace nada. Invalide `OnBeforeChangeTool` el método en `CMFCToolBarsCustomizeDialog` una clase derivada de si desea realizar el procesamiento antes de que se produzca un cambio en una herramienta de usuario, como liberar recursos que *pSelTool* utiliza.

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Inicia un editor de imágenes para que un usuario pueda personalizar un botón de barra de herramientas o un icono de elemento de menú.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la ventana primaria.

*Bits*<br/>
[en] Una referencia a un objeto de mapa de bits que se va a editar.

*nBitsPerPixel*<br/>
[en] Resolución de color de mapa de bits, en bits por píxel.

### <a name="return-value"></a>Valor devuelto

TRUESi se está confirmando un cambio; de lo contrario FALSO. La implementación predeterminada muestra un cuadro de diálogo y devuelve TRUE si el usuario hace clic en **Aceptar**o FALSE si el usuario hace clic en **Cancelar** o en el botón **Cerrar.**

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando el usuario ejecuta el editor de imágenes. La implementación predeterminada muestra [CMFCImageEditorDialog cuadro de](../../mfc/reference/cmfcimageeditordialog-class.md) diálogo de la clase. Reemplazar `OnEditToolbarMenuImage` en una clase derivada para usar un editor de imágenes personalizado.

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog

Reemplazaciones para aumentar la inicialización de la hoja de propiedades.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

El resultado de llamar a la [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) método.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base, [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), mostrando el botón **Cerrar,** asegurándose de que el cuadro de diálogo se ajusta al tamaño de pantalla actual y moviendo el botón **Ayuda** a la esquina inferior izquierda del cuadro de diálogo.

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage

Controla la notificación del marco de trabajo de que la página **Herramientas** está a punto de inicializarse.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada. Invalide este método en una clase derivada para procesar esta notificación.

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy

Llamado por el marco de trabajo después de que la ventana se ha destruido.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base, `CPropertySheet::PostNcDestroy`, restaurando la aplicación al modo anterior.

El [CMFCToolBarsCustomizeDialog::Create](#create) método coloca la aplicación en un modo especial que limita al usuario a las tareas de personalización.

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton

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
[en] Especifica el identificador de categoría del que se va a quitar el botón.

*uiCmdId*<br/>
[en] Especifica el identificador de comando del botón.

*lpszCategory*<br/>
[en] Especifica el nombre de la categoría de la que se va a quitar el botón.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del botón quitado, o -1 si el identificador de comando especificado no se encontró en la categoría especificada. Si *uiCategoryId* es -1, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

Para quitar un botón de todas las categorías, llame a la primera sobrecarga de este método y establezca *uiCategoryId* en -1.

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::RenameCategory

Cambia el nombre de una categoría en el cuadro de lista de categorías de la página **Comandos.**

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parámetros

*lpszCategoryOld*<br/>
[en] El nombre de la categoría que se debe cambiar.

*lpszCategoryNew*<br/>
[en] El nuevo nombre de categoría.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El nombre de la categoría debe ser único.

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton

Reemplaza un botón de barra de herramientas en el cuadro de lista de comandos de la página **Comandos.**

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] Especifica el comando del botón que se va a reemplazar.

*Botón*<br/>
[en] Una referencia **const** al objeto de botón de barra de herramientas que reemplaza el botón antiguo.

### <a name="remarks"></a>Observaciones

Cuando [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), o [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) agrega un comando a la **comandos** página, ese comando tiene la forma de un [CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md) objeto (o un [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md) objeto para un elemento de menú que contiene un submenú agregado por `AddMenuCommands`). El marco de trabajo también llama a estos tres métodos para agregar comandos automáticamente. Si desea que un comando se represente mediante `ReplaceButton` un tipo derivado en su lugar, llame y pase un botón del tipo derivado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `ReplaceButton` muestra `CMFCToolBarsCustomizeDialog` cómo utilizar el método en la clase. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory

Especifica qué categoría de la lista de categorías de la página **Comandos** es la categoría de usuario. Debe llamar a esta función antes de llamar a [CMFCToolBarsCustomizeDialog::Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parámetros

*lpszCategory*<br/>
[en] El nombre de la categoría.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El marco de trabajo no utiliza actualmente la configuración de categoría de usuario.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)
