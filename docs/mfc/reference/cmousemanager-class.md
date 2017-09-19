---
title: Clase CMouseManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- CMouseManager class
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7ba50f976f6cf9d6b701e39304c50507cfa34cc5
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmousemanager-class"></a>Clase CMouseManager
Permite al asociar diferentes comandos a un determinado usuario [CView](../../mfc/reference/cview-class.md) objeto cuando el usuario hace doble clic dentro de esa vista.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|Agrega un `CView` objeto a la **personalización** cuadro de diálogo. El **personalización** cuadro de diálogo permite al usuario asociar un doble clic a un comando para cada una de las vistas de lista.|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.|  
|[CMouseManager::GetViewIconId](#getviewiconid)|Devuelve el icono asociado al identificador de vista proporcionado.|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Devuelve el identificador de vista asociado con el nombre de vista proporcionado.|  
|[CMouseManager::GetViewNames](#getviewnames)|Recupera una lista de todos los nombres de vista agregada.|  
|[CMouseManager::LoadState](#loadstate)|Carga el `CMouseManager` estado del registro de Windows.|  
|[CMouseManager::SaveState](#savestate)|Escribe el `CMouseManager` estado al registro de Windows.|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Asocia el comando proporcionado y la vista proporcionada.|  
  
## <a name="remarks"></a>Comentarios  
 El `CMouseManager` clase mantiene una colección de `CView` objetos. Cada vista se identifica mediante un nombre y con un Id. Estas vistas se muestran en la **personalización** cuadro de diálogo. El usuario puede cambiar el comando que está asociado a ninguna vista a través de la **personalización** cuadro de diálogo. Cuando el usuario hace doble clic en esa vista, se ejecuta el comando asociado. Para admitir esto desde una perspectiva de programación, debe procesar la `WM_LBUTTONDBLCLK` mensaje y llamar a la [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) función en el código para que `CView` objeto...  
  
 No debería crear un `CMouseManager` objeto manualmente. Se creará el marco de la aplicación. También se destruirá automáticamente cuando el usuario sale de la aplicación. Para obtener un puntero al administrador del mouse para la aplicación, llame a [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).  
  
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
 Nombre de una vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para admitir el comportamiento personalizado del mouse, se debe registrar una vista con el `CMouseManager` objeto. Cualquier objeto derivado de la `CView` clase se puede registrar con el administrador del mouse. La cadena y el icono asociado a una vista se muestran en la **Mouse** ficha de la **personalizar** cuadro de diálogo.  
  
 Es responsabilidad del programador para crear y mantener los identificadores de vista como `iViewId` y `iId`.  
  
 Para obtener más información acerca de cómo proporcionar un comportamiento personalizado de mouse, consulte [personalización del teclado y Mouse](../../mfc/keyboard-and-mouse-customization.md).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar un puntero a un `CMouseManager` objeto usando el `CWinAppEx::GetMouseManager` (método) y la `AddView` método en la `CMouseManager` clase. Este fragmento de código forma parte de la [muestra de recopilación de estado](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection Nº&4;](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand  
 Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro de la vista proporcionada.  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iId`  
 El identificador de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando si la vista está asociada a un comando; en caso contrario, 0.  
  
##  <a name="getviewiconid"></a>CMouseManager::GetViewIconId  
 Recupera el icono asociado a un identificador de la vista.  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iViewId`  
 El identificador de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de recurso de icono, si es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método se producirá un error si la vista no está registrada en primer lugar mediante [CMouseManager::AddView](#addview).  
  
##  <a name="getviewidbyname"></a>CMouseManager::GetViewIdByName  
 Recupera el identificador de vista asociado con un nombre de vista.  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 El nombre de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de la vista si es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método busca a través de vistas registradas mediante [CMouseManager::AddView](#addview).  
  
##  <a name="getviewnames"></a>CMouseManager::GetViewNames  
 Recupera una lista de todos los nombres de vista registrado.  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `listOfNames`  
 Una referencia a `CStringList` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método rellena el parámetro `listOfNames` con los nombres de todas las vistas que se registran mediante [CMouseManager::AddView](#addview).  
  
##  <a name="loadstate"></a>CMouseManager::LoadState  
 Carga el estado de la [CMouseManager clase](../../mfc/reference/cmousemanager-class.md) desde el registro.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Ruta de acceso de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La información de estado que se carga desde el registro incluye las vistas registradas, identificadores de vista y los comandos asociados. Si el parámetro `lpszProfileName` es `NULL`, esta función carga la `CMouseManager` datos desde la ubicación de registro predeterminado controlada por el [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
 En la mayoría de los casos, no es necesario llamar directamente a esta función. Se llama como parte del proceso de inicialización del área de trabajo. Para obtener más información sobre el proceso de inicialización del área de trabajo, consulte [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).  
  
##  <a name="savestate"></a>CMouseManager::SaveState  
 Escribe el estado de la [CMouseManager clase](../../mfc/reference/cmousemanager-class.md) en el registro.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Ruta de acceso de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La información de estado que se escriben en el registro incluye vistas de todos los identificadores de vista y los comandos asociados. Si el parámetro `lpszProfileName` es `NULL`, esta función se escribe el `CMouseManager` datos a la ubicación de registro predeterminado controlada por el [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
 En la mayoría de los casos, no es necesario llamar directamente a esta función. Se llama como parte del proceso de serialización de área de trabajo. Para obtener más información sobre el proceso de serialización de área de trabajo, consulte [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
##  <a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk  
 Asocia un comando personalizado a una vista que primero se registra con el Administrador de mouse.  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iViewId`  
 Identificador de la vista.  
  
 [in] `uiCmd`  
 El identificador de comando.  
  
### <a name="remarks"></a>Comentarios  
 Para asociar un comando personalizado a una vista, debe registrar primero la vista con [CMouseManager::AddView](#addview). El `AddView` método requiere un identificador de la vista como un parámetro de entrada. Una vez que registra una vista, puede llamar a `CMouseManager::SetCommandForDblClk` con la misma vista identificador parámetro de entrada que ha proporcionado a `AddView`. Posteriormente, cuando el usuario hace doble clic del mouse en la vista registrado, la aplicación ejecutará el comando indicado por `uiCmd.` para admitir el comportamiento personalizado del mouse, también debe personalizar la vista registrada con el administrador del mouse. Para obtener más información sobre el comportamiento personalizado del mouse, consulte [personalización del teclado y Mouse]--brokenlink--(.. / customization.md de mouse y teclado).  
  
 Si `uiCmd` está establecido en 0, la vista especificada ya no está asociada con un comando.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Personalización del teclado y Mouse](../../mfc/keyboard-and-mouse-customization.md)




