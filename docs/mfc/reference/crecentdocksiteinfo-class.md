---
title: Clase CRecentDockSiteInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::CleanUp
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDefaultPaneDivider
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedPercent
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedRect
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentListOfPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentPaneContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentTabContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::Init
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::IsRecentLeftPane
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SaveListOfRecentPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SetInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::StoreDockInfo
dev_langs:
- C++
helpviewer_keywords:
- CRecentDockSiteInfo class
ms.assetid: 2dd14f95-d5a2-4461-a7a5-2c6c36a3a165
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
ms.openlocfilehash: ae700ae78485ca4e5cfd68da0d0ae1448d1f1d5d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="crecentdocksiteinfo-class"></a>Clase CRecentDockSiteInfo
El `CRecentDockSiteInfo` clase es una clase auxiliar que almacena información de estado reciente para el [CPane clase](../../mfc/reference/cpane-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRecentDockSiteInfo : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRecentDockSiteInfo::CleanUp](#cleanup)||  
|[CRecentDockSiteInfo::GetRecentDefaultPaneDivider](#getrecentdefaultpanedivider)||  
|[CRecentDockSiteInfo::GetRecentDockedPercent](#getrecentdockedpercent)||  
|[CRecentDockSiteInfo::GetRecentDockedRect](#getrecentdockedrect)||  
|[CRecentDockSiteInfo::GetRecentListOfPanes](#getrecentlistofpanes)||  
|[CRecentDockSiteInfo::GetRecentPaneContainer](#getrecentpanecontainer)||  
|[CRecentDockSiteInfo::GetRecentTabContainer](#getrecenttabcontainer)||  
|[CRecentDockSiteInfo::Init](#init)||  
|[CRecentDockSiteInfo::IsRecentLeftPane](#isrecentleftpane)||  
|[CRecentDockSiteInfo::operator =](#operator_eq)||  
|[CRecentDockSiteInfo::SaveListOfRecentPanes](#savelistofrecentpanes)||  
|[CRecentDockSiteInfo::SetInfo](#setinfo)||  
|[CRecentDockSiteInfo::StoreDockInfo](#storedockinfo)||  
  
## <a name="remarks"></a>Comentarios  
 La clase `CRecentDockSiteInfo` es una clase de administración de datos. Realiza un seguimiento del último estado de `CPane` durante su transición entre acoplado y flotante. Cuando un usuario hace doble clic en un panel acoplable flotante, se acopla. Si hace doble clic en el panel acoplado, vuelve a su ubicación, tamaño y estado anteriores. De forma similar, cuando el panel se vuelve a acoplar, regresa a su ubicación de acoplamiento anterior. Esta clase de datos es lo que hace que sea posible. Dado que los miembros de esta clase almacenan información de estado del panel acoplado, la aplicación no debe modificarlos directamente.  
  
 Se crea un objeto `CRecentDockSiteInfo` cada vez que se crea un panel. Cada `CPane` objeto tiene una variable de miembro [CPane::m_recentDockInfo](../../mfc/reference/cpane-class.md#m_recentdockinfo), para almacenar esta información.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrecentDockSiteInfo.h  
  
##  <a name="cleanup"></a>CRecentDockSiteInfo::CleanUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void CleanUp();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="crecentdocksiteinfo"></a>CRecentDockSiteInfo::CRecentDockSiteInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrecentdefaultpanedivider"></a>CRecentDockSiteInfo::GetRecentDefaultPaneDivider  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CPaneDivider* GetRecentDefaultPaneDivider();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrecentdockedpercent"></a>CRecentDockSiteInfo::GetRecentDockedPercent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetRecentDockedPercent(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bForSlider`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrecentdockedrect"></a>CRecentDockSiteInfo::GetRecentDockedRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect& GetRecentDockedRect(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bForSlider`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrecentlistofpanes"></a>CRecentDockSiteInfo::GetRecentListOfPanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CList<HWND, HWND>& GetRecentListOfPanes(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bForSlider`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrecentpanecontainer"></a>CRecentDockSiteInfo::GetRecentPaneContainer  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CPaneContainer* GetRecentPaneContainer(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bForSlider`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrecenttabcontainer"></a>CRecentDockSiteInfo::GetRecentTabContainer  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CPaneContainer* GetRecentTabContainer(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bForSlider`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="init"></a>CRecentDockSiteInfo::Init  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Init();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isrecentleftpane"></a>CRecentDockSiteInfo::IsRecentLeftPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsRecentLeftPane(BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bForSlider`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="operator_eq"></a>CRecentDockSiteInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRecentDockSiteInfo& operator=(CRecentDockSiteInfo& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="savelistofrecentpanes"></a>CRecentDockSiteInfo::SaveListOfRecentPanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SaveListOfRecentPanes(CList<HWND,  
    HWND>& lstOrg,  
    BOOL bForSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CList<HWND`  
 [in] `lstOrg`  
 [in] `bForSlider`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setinfo"></a>CRecentDockSiteInfo::SetInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetInfo(
    BOOL bForSlider,  
    CRecentDockSiteInfo& srcInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bForSlider`  
 [in] `srcInfo`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="storedockinfo"></a>CRecentDockSiteInfo::StoreDockInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void StoreDockInfo(
    CPaneContainer* pRecentContainer,  
    CDockablePane* pTabbedBar = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRecentContainer`  
 [in] `pTabbedBar`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CDockSite](../../mfc/reference/cdocksite-class.md)

