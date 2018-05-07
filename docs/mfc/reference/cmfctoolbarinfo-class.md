---
title: Clase CMFCToolBarInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de968fe53348b4cfa3f46e999da37cdca6f88c90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctoolbarinfo-class"></a>Clase CMFCToolBarInfo
Contiene los identificadores de recursos de las imágenes de la barra de herramientas en diversos estados. `CMFCToolBarInfo` es una clase auxiliar que se utiliza como un parámetro de la [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas (inactiva) regular.|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas deshabilitada.|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas (activos) seleccionada.|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas de gran tamaño, regular.|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene grandes, deshabilitar imágenes de barra de herramientas.|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas de gran tamaño, seleccionado.|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene imágenes de menú deshabilitado.|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Id. de recurso del mapa de bits de barra de herramientas que contiene imágenes de menú.|  
  
## <a name="remarks"></a>Comentarios  
 Un mapa de bits de barra de herramientas completa está formada por imágenes pequeñas de la barra de herramientas (botones) de un tamaño fijo. Cada identificador de recurso que se almacena en un `CMFCToolBarInfo` objeto es un mapa de bits que contiene un conjunto completo de las imágenes de barra de herramientas en un único estado (por ejemplo, seleccionado, deshabilitado, grande o imágenes de menú).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbar.h  
  
##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID  
 Especifica un identificador de recurso para todas las imágenes de botón normal de una barra de herramientas.  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID  
 Especifica un identificador de recurso para las imágenes no está disponible el botón de una barra de herramientas.  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID  
 Especifica un identificador de recurso para todas las imágenes de botón resaltado de una barra de herramientas.  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID  
 Especifica un identificador de recurso para todas las imágenes de gran tamaño de botón normal de una barra de herramientas.  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID  
 Especifica un identificador de recurso para todas las imágenes de botón deshabilitado grandes de una barra de herramientas.  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID  
 Especifica un identificador de recurso para todas las imágenes resaltados grandes de una barra de herramientas.  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID  
 Especifica un identificador de recurso para las imágenes disponibles para el comando de una barra de herramientas.  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID  
 Especifica un identificador de recurso para todas las imágenes de una barra de herramientas de elemento de menú regular.  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
