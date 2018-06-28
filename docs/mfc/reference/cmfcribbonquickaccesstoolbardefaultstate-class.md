---
title: Clase CMFCRibbonQuickAccessToolBarDefaultState | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9fd8c983e0133644b6531e87f5fc1dec0fdc7b7
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041810"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>Clase CMFCRibbonQuickAccessToolBarDefaultState
Una clase auxiliar que administra el estado predeterminado para la barra de herramientas de acceso rápido que se coloca en la barra de cinta ( [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Construye un objeto `CMFCRibbonQuickAccessToolbarDefaultState`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Agrega un comando al estado predeterminado para la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Copia las propiedades de una barra de herramientas de acceso rápido a otra.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Quita todos los comandos de la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas.|  
  
## <a name="remarks"></a>Comentarios  
 Después de crear la barra de herramientas de acceso rápido en la aplicación, se recomienda que establezca su estado predeterminado mediante una llamada a [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Este estado predeterminado se restaura cuando un usuario hace clic en el **restablecer** situado en la **personalizar** página de la aplicación **opciones** cuadro de diálogo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonQuickAccessToolbarDefaultState` clase y cómo agregar un comando al estado predeterminado para la barra de herramientas de acceso rápido.  
  
 [!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonquickaccesstoolbar.h  
  
##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand  
 Agrega un comando al estado predeterminado para la barra de herramientas de acceso rápido.  
  
```  
void AddCommand(
    UINT uiCmd,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *[in] uiCmd*  
 Especifica el identificador del comando.  
  
 *[in] bIsVisible*  
 Establece la visibilidad del comando cuando la barra de herramientas de acceso rápido se encuentra en el estado predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Agregar un comando a la CMFCRibbonQuickAccessToolBarDefaultState lleva a cabo tres resultados. En primer lugar, cada comando agregado aparece en la lista desplegable del lado derecho de la barra de herramientas de acceso rápido. De esta manera, un usuario puede agregar o quitar el comando de la barra de herramientas de acceso rápido fácilmente. En segundo lugar, se restablece la barra de herramientas de acceso rápido para mostrar únicamente los comandos que se muestran como visible en el estado predeterminado cuando el usuario hace clic en el **restablecer** botón en el **personalizar** cuadro de diálogo. Tercero, si no ha llamado [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), la barra de herramientas de acceso rápido usa los comandos visibles en esta lista como los comandos visibles de forma predeterminada la primera vez que un usuario ejecuta la aplicación. Después de haber agregado todos los comandos que desee, llame a [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) para establecer esta instancia como el estado predeterminado para la barra de herramientas de acceso rápido de esa barra de cinta de opciones.  
  
##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom  
 Copia las propiedades de una barra de herramientas de acceso rápido a otra.  
  
```  
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *src*  
 Una referencia al origen de `CMFCRibbonQuickAccessToolBarDefaultState` objeto que lo copien.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia cada comando desde el origen de `CMFCRibbonQuickAccessToolBarDefaultState` objeto a este objeto mediante el uso de la [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) método.  
  
##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState  
 Construye el objeto de estado de la barra de herramientas de acceso rápido de forma predeterminada.  
  
```  
CMFCRibbonQuickAccessToolBarDefaultState();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, la lista de comandos que la nueva instancia de [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) contiene está vacío.  
  
##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll  
 Borra la lista de comandos de manera predeterminada en la barra de herramientas de acceso rápido.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función quita de la instancia de todos los comandos que las llamadas anteriores a [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) agregado.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
