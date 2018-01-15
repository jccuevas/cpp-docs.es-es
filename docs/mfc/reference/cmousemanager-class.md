---
title: Clase CMouseManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
dev_langs: C++
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f50b74731089346a9675b5340ba0ea1a0b2879f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmousemanager-class"></a>Clase CMouseManager
Permite que un usuario asociar diferentes comandos a un determinado [CView](../../mfc/reference/cview-class.md) objeto cuando el usuario hace doble clic dentro de esa vista.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|Agrega un `CView` el objeto a la **personalización** cuadro de diálogo. El **personalización** cuadro de diálogo permite al usuario asociar un doble clic a un comando para cada una de las vistas de lista.|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.|  
|[CMouseManager::GetViewIconId](#getviewiconid)|Devuelve el icono asociado al identificador de vista proporcionado.|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Devuelve el identificador de vista asociado con el nombre de vista proporcionado.|  
|[CMouseManager::GetViewNames](#getviewnames)|Recupera una lista de todos los nombres de vista agregada.|  
|[CMouseManager::LoadState](#loadstate)|Carga el `CMouseManager` estado del registro de Windows.|  
|[CMouseManager::SaveState](#savestate)|Escribe el `CMouseManager` estado en el registro de Windows.|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Asocia el comando proporcionado y la vista proporcionada.|  
  
## <a name="remarks"></a>Comentarios  
 El `CMouseManager` clase mantiene una colección de `CView` objetos. Cada vista se identifica mediante un nombre y un identificador. Estas vistas se muestran en la **personalización** cuadro de diálogo. El usuario puede cambiar el comando que está asociado a cualquier vista a través de la **personalización** cuadro de diálogo. Cuando el usuario hace doble clic en esa vista, se ejecuta el comando asociado. Para admitir esto desde una perspectiva de programación, debe procesar el `WM_LBUTTONDBLCLK` mensaje y llaman a la [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) función en el código para que `CView` objeto...  
  
 No debería crear un `CMouseManager` objeto manualmente. Se creará el marco de trabajo de la aplicación. También se destruirá automáticamente cuando el usuario cierra la aplicación. Para obtener un puntero al administrador de mouse (ratón) para la aplicación, llame a [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMouseManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmousemanager.h  
  
##  <a name="addview"></a>CMouseManager::AddView  
 Registra un [CView](../../mfc/reference/cview-class.md) objeto con el [CMouseManager clase](../../mfc/reference/cmousemanager-class.md) para admitir el comportamiento personalizado del mouse.  
  
```  
BOOL AddView(
    int iViewId,  
    UINT uiViewNameResId,  
    UINT uiIconId = 0);

 
BOOL AddView(
    int iId,  
    LPCTSTR lpszViewName,  
    UINT uiIconId = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iViewId`  
 Un identificador de la vista.  
  
 [in] `uiViewNameResId`  
 Un identificador de cadena de recurso al que hace referencia el nombre de vista.  
  
 [in] `uiIconId`  
 Un identificador de icono de vista.  
  
 [in] `iId`  
 Un identificador de la vista.  
  
 [in] `lpszViewName`  
 Un nombre de vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para admitir el comportamiento personalizado del mouse, una vista debe estar registrada con el `CMouseManager` objeto. Cualquier objeto derivado de la `CView` clase se puede registrar con el Administrador de mouse (ratón). La cadena y el icono asociado a una vista se muestran en la **Mouse** pestaña de la **personalizar** cuadro de diálogo.  
  
 Es responsabilidad del programador para crear y mantener vista identificadores como `iViewId` y `iId`.  
  
 Para obtener más información acerca de cómo proporcionar un comportamiento personalizado del mouse, consulte [personalización del teclado y mouse (ratón)](../../mfc/keyboard-and-mouse-customization.md).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar un puntero a un `CMouseManager` objeto mediante el uso de la `CWinAppEx::GetMouseManager` método y `AddView` método en la `CMouseManager` clase. Este fragmento de código forma parte de la [ejemplo de la colección de estados](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand  
 Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iId`  
 El identificador de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando si la vista está asociada a un comando; en caso contrario es 0.  
  
##  <a name="getviewiconid"></a>CMouseManager::GetViewIconId  
 Recupera el icono asociado con un identificador de la vista.  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iViewId`  
 El identificador de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de recurso de icono, si se realiza correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método se producirá un error si la vista no se registraron por primera vez mediante el uso de [CMouseManager::AddView](#addview).  
  
##  <a name="getviewidbyname"></a>CMouseManager::GetViewIdByName  
 Recupera el identificador de vista asociado con un nombre de vista.  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 El nombre de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de la vista si se realiza correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método busca a través de vistas que se registró mediante [CMouseManager::AddView](#addview).  
  
##  <a name="getviewnames"></a>CMouseManager::GetViewNames  
 Recupera una lista de todos los nombres de vista registrados.  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `listOfNames`  
 Una referencia a `CStringList` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método rellena el parámetro `listOfNames` con los nombres de todas las vistas que se registró mediante [CMouseManager::AddView](#addview).  
  
##  <a name="loadstate"></a>CMouseManager::LoadState  
 Carga el estado de la [CMouseManager clase](../../mfc/reference/cmousemanager-class.md) desde el registro.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Una ruta de acceso de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La información de estado cargada desde el registro incluye las vistas registradas, identificadores de la vista y los comandos asociados. Si el parámetro `lpszProfileName` es `NULL`, esta función carga la `CMouseManager` datos desde la ubicación de registro predeterminado controlada por el [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
 En la mayoría de los casos, no es necesario llamar directamente a esta función. Se llama como parte del proceso de inicialización de área de trabajo. Para obtener más información sobre el proceso de inicialización del área de trabajo, consulte [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).  
  
##  <a name="savestate"></a>CMouseManager::SaveState  
 Escribe el estado de la [CMouseManager clase](../../mfc/reference/cmousemanager-class.md) en el registro.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Una ruta de acceso de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La información de estado que se escribe en el registro incluye vistas todas las registradas, identificadores de la vista y los comandos asociados. Si el parámetro `lpszProfileName` es `NULL`, esta función escribe la `CMouseManager` datos a la ubicación de registro predeterminado controlada por el [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
 En la mayoría de los casos, no es necesario llamar directamente a esta función. Se llama como parte del proceso de serialización de área de trabajo. Para obtener más información sobre el proceso de serialización de área de trabajo, consulte [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
##  <a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk  
 Asocia un comando personalizado a una vista que se registraron por primera vez con el Administrador de mouse (ratón).  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iViewId`  
 El identificador de la vista.  
  
 [in] `uiCmd`  
 El identificador de comando.  
  
### <a name="remarks"></a>Comentarios  
 Para asociar un comando personalizado a una vista, primero debe registrar la vista mediante el uso de [CMouseManager::AddView](#addview). El `AddView` método requiere un identificador de la vista como un parámetro de entrada. Una vez que registra una vista, puede llamar a `CMouseManager::SetCommandForDblClk` con la misma vista identificador parámetro de entrada que ha proporcionado para `AddView`. Por lo tanto, cuando el usuario hace doble clic del mouse en la vista registrado, la aplicación ejecutará el comando indicado por `uiCmd.` para admitir el comportamiento personalizado del mouse, también necesitará personalizar la vista registrada con el Administrador de mouse (ratón). Para obtener más información acerca del comportamiento del mouse personalizados, consulte brokenlink [personalización del teclado y mouse (ratón)]----(.. / customization.md de mouse y teclado).  
  
 Si `uiCmd` se establece en 0, ya no está asociada a un comando de la vista especificada.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Personalización del teclado y del mouse](../../mfc/keyboard-and-mouse-customization.md)



