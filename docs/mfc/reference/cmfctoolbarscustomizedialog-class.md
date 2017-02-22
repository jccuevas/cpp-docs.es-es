---
title: "CMFCToolBarsCustomizeDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarsCustomizeDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarsCustomizeDialog class"
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCToolBarsCustomizeDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un cuadro de diálogo no modal de tabulación \([CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)\) que permite al usuario personalizar barras de herramientas, menús, los métodos abreviados de teclado, las herramientas definido por el usuario, y el estilo visual en una aplicación.  Normalmente, el usuario tiene acceso a este cuadro de diálogo **Personalizar** seleccionando en el menú de **Herramientas** .  
  
 El cuadro de diálogo de **Personalizar** tiene seis pestañas: comandos, **barras de herramientas**, **Herramientas**, **Teclado**, **Menú**, y **Opciones**.  
  
## Sintaxis  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](../Topic/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog.md)|Crea un objeto `CMFCToolBarsCustomizeDialog`.|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](../Topic/CMFCToolBarsCustomizeDialog::AddButton.md)|Inserta un botón de la barra de herramientas de la lista de comandos en la página de Commandos|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](../Topic/CMFCToolBarsCustomizeDialog::AddMenu.md)|Carga un menú de los recursos y llama a [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md) para agregar ese menú a la lista de comandos en la página de Commandos.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md)|Carga un menú de los recursos y llama a [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md) para agregar ese menú a la lista de comandos en la página de Commandos.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](../Topic/CMFCToolBarsCustomizeDialog::AddToolBar.md)|carga una barra de herramientas de los recursos.  A continuación, porque cada comando del menú llama al método de [CMFCToolBarsCustomizeDialog::AddButton](../Topic/CMFCToolBarsCustomizeDialog::AddButton.md) para insertar un botón en la lista de comandos en la página de Commandos bajo la categoría especificada.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md)|Muestra el cuadro de diálogo de **personalización** .|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|Reservado para uso futuro.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](../Topic/CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars.md)|Habilita o deshabilita crear nuevas barras de herramientas mediante el cuadro de diálogo **Personalizar** .|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](../Topic/CMFCToolBarsCustomizeDialog::FillAllCommandsList.md)|Rellena el objeto proporcionado de `CListBox` con los comandos de la categoría de **Todos los comandos** .|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](../Topic/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox.md)|Rellena el objeto proporcionado de `CComboBox` con el nombre de cada categoría de comando en el cuadro de diálogo de **Personalizar** .|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](../Topic/CMFCToolBarsCustomizeDialog::FillCategoriesListBox.md)|Rellena el objeto proporcionado de `CListBox` con el nombre de cada categoría de comando en el cuadro de diálogo de **Personalizar** .|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](../Topic/CMFCToolBarsCustomizeDialog::GetCommandName.md)|Recupera el nombre que está asociado con la identificación especificada de comando|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](../Topic/CMFCToolBarsCustomizeDialog::GetCountInCategory.md)|Recupera el número de elementos en la lista proporcionada que tienen una etiqueta de texto determinado.|  
|[CMFCToolBarsCustomizeDialog::GetFlags](../Topic/CMFCToolBarsCustomizeDialog::GetFlags.md)|Recupera el conjunto de indicadores que afectan al comportamiento del cuadro de diálogo.|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](../Topic/CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage.md)|Inicia un editor de imágenes de modo que un usuario puede personalizar un icono de botón de la barra de herramientas o el elemento de menú.|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](../Topic/CMFCToolBarsCustomizeDialog::OnInitDialog.md)|reemplaza para aumentar la inicialización de la hoja de propiedades.  \(Reemplaza [CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md).\)|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](../Topic/CMFCToolBarsCustomizeDialog::PostNcDestroy.md)|Llamado por el marco una vez que la ventana.  \(Reemplaza `CPropertySheet::PostNcDestroy`.\)|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](../Topic/CMFCToolBarsCustomizeDialog::RemoveButton.md)|Quita el botón con el identificador especificado de comando de la categoría especificada, o de todas las categorías.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](../Topic/CMFCToolBarsCustomizeDialog::RenameCategory.md)|Cambia el nombre de una categoría del cuadro de lista de categorías en la pestaña de Commandos.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md)|Reemplaza un botón en la lista de comandos en la pestaña de Commandos con un nuevo objeto de botón de la barra de herramientas.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](../Topic/CMFCToolBarsCustomizeDialog::SetUserCategory.md)|Agrega una categoría a la lista de categorías que aparezcan en la ficha de Commandos.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](../Topic/CMFCToolBarsCustomizeDialog::CheckToolsValidity.md)|Llamado por el marco para determinar si la lista de herramientas definido por el usuario es válida.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](../Topic/CMFCToolBarsCustomizeDialog::OnAfterChangeTool.md)|Llamado por el marco cuando las propiedades de un cambio de herramienta definido por el usuario.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](../Topic/CMFCToolBarsCustomizeDialog::OnAssignKey.md)|Determina si un método abreviado de teclado especificado se puede asignar a una acción.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](../Topic/CMFCToolBarsCustomizeDialog::OnBeforeChangeTool.md)|Determina si una herramienta definido por el usuario puede cambiar.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](../Topic/CMFCToolBarsCustomizeDialog::OnInitToolsPage.md)|Llamado por el marco cuando el usuario elige se solicita la pestaña de **Herramientas** .|  
  
## Comentarios  
 Para mostrar el cuadro de diálogo de **Personalizar** , cree un objeto de `CMFCToolBarsCustomizeDialog` y llame al método Create.  
  
 Mientras el cuadro de diálogo de **Personalizar** está activa, la aplicación funciona en un modo especial que limite a las tareas de personalización.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCToolBarsCustomizeDialog` .  El ejemplo muestra cómo reemplazar un botón de la barra de herramientas en el cuadro de lista de comandos en la página de Commandos, habilitar crear nuevas barras de herramientas mediante el cuadro de diálogo **Personalizar** , y mostrar el cuadro de diálogo de **personalización** .  Este fragmento de código es parte de [Ejemplo de demostración de IE](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/CPP/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)  
  
## Requisitos  
 **encabezado:** afxToolBarsCustomizeDialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)