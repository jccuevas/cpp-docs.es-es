---
title: Clase CMFCToolBarInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCToolBarInfo class
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: 22
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: a9e66ffa0b5a751a7e5711ed20927a6adcede45d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarinfo-class"></a>Clase CMFCToolBarInfo
Contiene los identificadores de recursos de las imágenes de la barra de herramientas en diversos estados. `CMFCToolBarInfo`es una clase auxiliar que se utiliza como un parámetro de la [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Identificador de recurso de mapa de bits de barra de herramientas que contiene imágenes de barra de herramientas (frío) regular.|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Identificador de recurso de mapa de bits de barra de herramientas que contiene imágenes de barras de herramientas.|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Identificador de recurso de mapa de bits de barra de herramientas que contiene las imágenes de la barra de herramientas seleccionada (activos).|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Identificador de recurso de mapa de bits de barra de herramientas que contiene imágenes grandes, regular de barra de herramientas.|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Identificador del recurso de mapa de bits de barra de herramientas que contiene grandes, deshabilitado imágenes de la barra de herramientas.|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Identificador de recurso de mapa de bits de barra de herramientas que contiene imágenes grandes de barra de herramientas seleccionado.|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Identificador de recurso de mapa de bits de barra de herramientas que contiene imágenes de menú deshabilitado.|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Identificador de recurso de mapa de bits de barra de herramientas que contiene imágenes de menú.|  
  
## <a name="remarks"></a>Comentarios  
 Un mapa de bits de barra de herramientas completa está formada por imágenes pequeñas de la barra de herramientas (botones) de un tamaño fijo. Cada identificador de recurso que se almacena en un `CMFCToolBarInfo` objeto es un mapa de bits que contiene un conjunto completo de las imágenes de la barra de herramientas en un único estado (por ejemplo, seleccionado, deshabilitado, grande o imágenes de menú).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbar.h  
  
##  <a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID  
 Especifica un identificador de recurso para todas las imágenes de botón normal de una barra de herramientas.  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID  
 Especifica un identificador de recurso para las imágenes no está disponible el botón de barra de herramientas.  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID  
 Especifica un identificador de recurso para todas las imágenes de botón resaltado de una barra de herramientas.  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID  
 Especifica un identificador de recurso para todas las imágenes de gran tamaño de botón normal de una barra de herramientas.  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID  
 Especifica un identificador de recurso para todas las imágenes de gran tamaño de botón deshabilitado de una barra de herramientas.  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID  
 Especifica un identificador de recurso para todas las imágenes resaltadas grandes de una barra de herramientas.  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID  
 Especifica un identificador de recurso para las imágenes disponibles para el comando de barra de herramientas.  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID  
 Especifica un identificador de recurso para todas las imágenes de elemento de menú normal de una barra de herramientas.  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

