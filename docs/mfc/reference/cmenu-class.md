---
title: "CMenu Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMenu class"
  - "HMENU"
  - "menús, clase base"
  - "menús, class"
  - "menús, crear"
  - "menús, administrar"
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una encapsulación de Windows `HMENU`.  
  
## Sintaxis  
  
```  
class CMenu : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMenu::CMenu](../Topic/CMenu::CMenu.md)|Crea un objeto `CMenu`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)|Agrega un nuevo elemento al final de este menú.|  
|[CMenu::Attach](../Topic/CMenu::Attach.md)|Asocia un identificador de menú de Windows a un objeto de `CMenu` .|  
|[CMenu::CheckMenuItem](../Topic/CMenu::CheckMenuItem.md)|Coloca una marca de verificación junto a o quita una marca de verificación de un elemento de menú del menú emergente.|  
|[CMenu::CheckMenuRadioItem](../Topic/CMenu::CheckMenuRadioItem.md)|Coloca un botón de radio en un elemento de menú y quita el botón de opción de todos los demás elementos de menú del grupo.|  
|[CMenu::CreateMenu](../Topic/CMenu::CreateMenu.md)|Crea un menú vacío y lo asocia a un objeto de `CMenu` .|  
|[CMenu::CreatePopupMenu](../Topic/CMenu::CreatePopupMenu.md)|Crea un menú emergente vacío y lo asocia a un objeto de `CMenu` .|  
|[CMenu::DeleteMenu](../Topic/CMenu::DeleteMenu.md)|Elimina un elemento especificado del menú.  Si el elemento de menú tiene un menú emergente asociado, destruye el identificador al menú emergente y libera la memoria utilizada por ella.|  
|[CMenu::DeleteTempMap](../Topic/CMenu::DeleteTempMap.md)|Elimina cualquier objeto temporal de `CMenu` creado por la función miembro de `FromHandle` .|  
|[CMenu::DestroyMenu](../Topic/CMenu::DestroyMenu.md)|Destruye el menú asociado a un objeto de `CMenu` y libera la memoria que el menú ocupara.|  
|[CMenu::Detach](../Topic/CMenu::Detach.md)|Desasocia un identificador de menú de Windows de un objeto de `CMenu` y devuelve el identificador.|  
|[CMenu::DrawItem](../Topic/CMenu::DrawItem.md)|Llamado por el marco cuando un aspecto visual de los cambios propietario\-drenados de un menú.|  
|[CMenu::EnableMenuItem](../Topic/CMenu::EnableMenuItem.md)|Los permisos, neutralizaciones, o atenuadas \(los grises\) un elemento de menú.|  
|[CMenu::FromHandle](../Topic/CMenu::FromHandle.md)|Devuelve un puntero a un objeto de `CMenu` dado un identificador de menú de Windows.|  
|[CMenu::GetDefaultItem](../Topic/CMenu::GetDefaultItem.md)|determina el elemento de menú predeterminado en el menú especificado.|  
|[CMenu::GetMenuContextHelpId](../Topic/CMenu::GetMenuContextHelpId.md)|Recupera el Id. de contexto de ayuda asociado al menú.|  
|[CMenu::GetMenuInfo](../Topic/CMenu::GetMenuInfo.md)|Recupera información en un menú concreto.|  
|[CMenu::GetMenuItemCount](../Topic/CMenu::GetMenuItemCount.md)|Determina el número de elementos de un menú emergente o de nivel superior.|  
|[CMenu::GetMenuItemID](../Topic/CMenu::GetMenuItemID.md)|Obtiene el identificador del elemento de menú para un elemento de menú ubicado en la posición especificada.|  
|[CMenu::GetMenuItemInfo](../Topic/CMenu::GetMenuItemInfo.md)|Recupera información sobre un elemento de menú.|  
|[CMenu::GetMenuState](../Topic/CMenu::GetMenuState.md)|Devuelve el estado del elemento de menú especificado o el número de elementos de un menú emergente.|  
|[CMenu::GetMenuString](../Topic/CMenu::GetMenuString.md)|Recupera la etiqueta de elemento de menú especificado.|  
|[CMenu::GetSafeHmenu](../Topic/CMenu::GetSafeHmenu.md)|Devuelve `m_hMenu` ajustará en este objeto de `CMenu` .|  
|[CMenu::GetSubMenu](../Topic/CMenu::GetSubMenu.md)|Recupera un puntero a un menú emergente.|  
|[CMenu::InsertMenu](../Topic/CMenu::InsertMenu.md)|Inserta un nuevo elemento de menú en la posición especificada, moviendo otros elementos desde el menú.|  
|[CMenu::InsertMenuItem](../Topic/CMenu::InsertMenuItem.md)|Inserta un nuevo elemento de menú en la posición especificada en un menú.|  
|[CMenu::LoadMenu](../Topic/CMenu::LoadMenu.md)|Carga un recurso de menú del archivo ejecutable y lo asocia a un objeto de `CMenu` .|  
|[CMenu::LoadMenuIndirect](../Topic/CMenu::LoadMenuIndirect.md)|Carga un menú de una plantilla de menú en memoria y lo asocia a un objeto de `CMenu` .|  
|[CMenu::MeasureItem](../Topic/CMenu::MeasureItem.md)|Llamado por el marco para determinar dimensiones de menú al menú propietario\- dibujado.|  
|[CMenu::ModifyMenu](../Topic/CMenu::ModifyMenu.md)|Cambia un elemento de menú existente en la posición especificada.|  
|[CMenu::RemoveMenu](../Topic/CMenu::RemoveMenu.md)|Elimina un elemento de menú a un menú emergente asociado de menú especificado.|  
|[CMenu::SetDefaultItem](../Topic/CMenu::SetDefaultItem.md)|establece el elemento de menú predeterminado para el menú especificado.|  
|[CMenu::SetMenuContextHelpId](../Topic/CMenu::SetMenuContextHelpId.md)|Establece el Id. de contexto de ayuda se asocie al menú.|  
|[CMenu::SetMenuInfo](../Topic/CMenu::SetMenuInfo.md)|Establece la información en un menú concreto.|  
|[CMenu::SetMenuItemBitmaps](../Topic/CMenu::SetMenuItemBitmaps.md)|Asocia los mapas de bits especificado de la marca de verificación a un elemento de menú.|  
|[CMenu::SetMenuItemInfo](../Topic/CMenu::SetMenuItemInfo.md)|Cambia la información de un elemento de menú.|  
|[CMenu::TrackPopupMenu](../Topic/CMenu::TrackPopupMenu.md)|Muestra un menú emergente flotante en la ubicación especificada y sigue la selección de elementos del menú emergente.|  
|[CMenu::TrackPopupMenuEx](../Topic/CMenu::TrackPopupMenuEx.md)|Muestra un menú emergente flotante en la ubicación especificada y sigue la selección de elementos del menú emergente.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMenu::operator HMENU](../Topic/CMenu::operator%20HMENU.md)|Recupera el identificador de objeto del menú.|  
|[CMenu::operator \!\=](../Topic/CMenu::operator%20!=.md)|Determina si dos objetos de menú no son iguales.|  
|[CMenu::operator \=\=](../Topic/CMenu::operator%20==.md)|Determina si dos objetos de menú son iguales.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMenu::m\_hMenu](../Topic/CMenu::m_hMenu.md)|Especifica el identificador al menú de Windows asociado al objeto de `CMenu` .|  
  
## Comentarios  
 Proporciona funciones miembro para crear, seguir, actualizar, y destruir un menú.  
  
 Cree un objeto de `CMenu` en el marco de pila como un valor local, entonces funciones miembro de entity\_CODECMenu call para manipular el nuevo menú según sea necesario.  A continuación, llamada [CWnd::SetMenu](../Topic/CWnd::SetMenu.md) para establecer el menú a una ventana, seguido inmediatamente por una llamada a la función miembro de [Desasociar](../Topic/CMenu::Detach.md) del objeto de `CMenu` .  La función miembro de `CWnd::SetMenu` establece el menú de la ventana al menú nuevo, hace que la ventana que se rediseñará para reflejar el cambio en el menú, y también pasa la propiedad del menú de la ventana.  La llamada a **Desasociar** desasocia `HMENU` del objeto de `CMenu` , para que cuando los pasos locales de la variable de `CMenu` fuera del ámbito, el destructor del objeto `CMenu` no intentan destruir un menú posee ya no.  El menú propio automáticamente se destruye cuando se destruye la ventana.  
  
 Puede utilizar la función miembro de [LoadMenuIndirect](../Topic/CMenu::LoadMenuIndirect.md) para crear un menú de una plantilla en memoria, pero un menú creado de un recurso por una llamada a [LoadMenu](../Topic/CMenu::LoadMenu.md) más fácilmente se mantiene, y el recurso propio de menú puede crear y modificar en el editor de menús.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo CTRLTEST de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo DYNAMENU de MFC](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)