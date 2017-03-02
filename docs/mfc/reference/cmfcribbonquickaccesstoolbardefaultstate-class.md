---
title: Clase CMFCRibbonQuickAccessToolBarDefaultState | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState class
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 211e8d897de923e7f07df389b0e9e7218cf45872
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>Clase CMFCRibbonQuickAccessToolBarDefaultState
Una clase auxiliar que administra el estado predeterminado para la barra de herramientas de acceso rápido que se coloca en la barra de cinta ( [CMFCRibbonBar clase](../../mfc/reference/cmfcribbonbar-class.md)).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Construye un objeto `CMFCRibbonQuickAccessToolbarDefaultState`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Agrega un comando al estado predeterminado para la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Copia las propiedades de una barra de herramientas de acceso rápido a otra.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Quita todos los comandos de la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Después de crear la barra de herramientas de acceso rápido en la aplicación, se recomienda establecer su estado predeterminado llamando [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Este estado predeterminado se restaura cuando un usuario hace clic en el **restablecer** situado en el **personalizar** página de la aplicación **opciones** cuadro de diálogo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonQuickAccessToolbarDefaultState` clase y cómo agregar un comando al estado predeterminado para la barra de herramientas de acceso rápido.  
  
 [!code-cpp[21 NVC_MFC_RibbonApp](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonquickaccesstoolbar.h  
  
##  <a name="a-nameaddcommanda--cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFCRibbonQuickAccessToolBarDefaultState::AddCommand  
 Agrega un comando al estado predeterminado para la barra de herramientas de acceso rápido.  
  
```  
void AddCommand(
    UINT uiCmd,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `[in] uiCmd`  
 Especifica el identificador del comando.  
  
 `[in] bIsVisible`  
 Establece la visibilidad del comando cuando la barra de herramientas de acceso rápido se encuentra en el estado predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Agregar un comando a la CMFCRibbonQuickAccessToolBarDefaultState realiza tres resultados. En primer lugar, cada comando agregado aparece en la lista desplegable en el lado derecho de la barra de herramientas de acceso rápido. De esta manera, un usuario puede agregar o quitar el comando de la barra de herramientas de acceso rápido. En segundo lugar, se restablece la barra de herramientas de acceso rápido para mostrar únicamente los comandos que aparecen como visible en el estado predeterminado cuando el usuario hace clic en el **restablecer** botón en la **personalizar** cuadro de diálogo. Tercero, si no ha llamado a [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), la barra de herramientas de acceso rápido usa los comandos visibles de esta lista como los comandos visibles de forma predeterminada la primera vez que un usuario ejecuta la aplicación. Después de haber agregado todos los comandos que desee, llamar a [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) para configurar esta instancia como el estado predeterminado para la barra de herramientas de acceso rápido de la barra de la cinta.  
  
##  <a name="a-namecopyfroma--cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom  
 Copia las propiedades de una barra de herramientas de acceso rápido a otra.  
  
```  
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Una referencia al origen de `CMFCRibbonQuickAccessToolBarDefaultState` objeto que se va a copiar de.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia cada comando desde el origen de `CMFCRibbonQuickAccessToolBarDefaultState` objeto a este objeto utilizando el [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) método.  
  
##  <a name="a-namecmfcribbonquickaccesstoolbardefaultstatea--cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState  
 Construye el objeto de estado de la barra de herramientas de acceso rápido de forma predeterminada.  
  
```  
CMFCRibbonQuickAccessToolBarDefaultState();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, la lista de comandos que la nueva instancia de [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) contiene está vacía.  
  
##  <a name="a-nameremovealla--cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll  
 Borra la lista de comandos de forma predeterminada en la barra de herramientas de acceso rápido.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función quita de esta instancia de todos los comandos que las llamadas anteriores a [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) agregado.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

