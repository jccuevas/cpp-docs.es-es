---
title: Clase CKeyFrame | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
dev_langs:
- C++
helpviewer_keywords:
- CKeyFrame class
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d8ecff2e36148fb114ee708712b6e8bd0fe558ed
ms.lasthandoff: 02/24/2017

---
# <a name="ckeyframe-class"></a>Clase CKeyFrame
Representa un fotograma clave de la animación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CKeyFrame::CKeyFrame](#ckeyframe)|Sobrecargado. Construye un fotograma clave que depende de otro fotogramas clave.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Agrega un fotograma clave a un guión gráfico. (Invalida [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|  
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Agrega un fotograma clave para el guión gráfico después de la transición.|  
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Agrega un fotograma clave para crear guiones gráficos en desplazamiento.|  
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Devuelve un puntero a un fotograma clave que depende de este fotograma clave.|  
|[CKeyFrame::GetOffset](#getoffset)|Devuelve un desplazamiento de otro fotogramas clave.|  
|[CKeyFrame::GetTransition](#gettransition)|Devuelve un puntero a una transición que depende de este fotograma clave.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CKeyFrame::m_offset](#m_offset)|Especifica el desplazamiento de este fotograma clave desde un fotograma clave que se almacena en m_pExistingKeyFrame.|  
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Almacena un puntero a un keframe existente. Este fotograma clave se agrega al guión gráfico con m_offset el fotograma clave existente.|  
|[CKeyFrame::m_pTransition](#m_ptransition)|Almacena un puntero a la transición que comienza en este fotograma clave.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase implementa un fotograma clave de animación. Un fotograma clave representa un momento determinado en un guión gráfico y puede utilizarse para especificar los tiempos de inicio y finalización de las transiciones. Un fotograma clave se basa en otro fotogramas clave y tener un desplazamiento (en segundos), o se puede basar en una transición y representa un momento cuando finaliza esta transición.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard  
 Agrega un fotograma clave a un guión gráfico.  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStoryboard`  
 Un puntero a un guión gráfico.  
  
 `bDeepAdd`  
 Especifica si desea agregar fotogramas clave o la transición de forma recursiva.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el fotograma clave se agregó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega un fotograma clave para el guión gráfico. Si depende de otros fotogramas clave o transición y bDeepAdd es TRUE, este método intenta agregarlos de forma recursiva.  
  
##  <a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition  
 Agrega un fotograma clave para el guión gráfico después de la transición.  
  
```  
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStoryboard`  
 Un puntero a un guión gráfico.  
  
 `bDeepAdd`  
 Especifica si desea agregar una transición de forma recursiva.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el fotograma clave se agregó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se llama el marco de trabajo para agregar un fotograma clave para el guión gráfico después de la transición.  
  
##  <a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset  
 Agrega un fotograma clave para crear guiones gráficos en desplazamiento.  
  
```  
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStoryboard`  
 Un puntero a un guión gráfico.  
  
 `bDeepAdd`  
 Especifica si este fotograma clave dependen de forma recursiva para agregar un fotograma clave.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el fotograma clave se agregó correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se llama el marco de trabajo para agregar un fotograma clave para crear guiones gráficos en desplazamiento.  
  
##  <a name="ckeyframe"></a>CKeyFrame::CKeyFrame  
 Construye un fotograma clave que depende de una transición.  
  
```  
CKeyFrame(CBaseTransition* pTransition);

 
CKeyFrame(
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTransition`  
 Un puntero a una transición.  
  
 `pKeyframe`  
 Puntero al fotograma clave.  
  
 `offset`  
 Desplazamiento, en segundos, desde el fotograma clave especificado por pKeyframe.  
  
### <a name="remarks"></a>Comentarios  
 El fotograma clave construido representa un momento determinado en un guión gráfico cuando finaliza la transición especificada.  
  
##  <a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe  
 Devuelve un puntero a un fotograma clave que depende de este fotograma clave.  
  
```  
CBaseKeyFrame* GetExistingKeyframe();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido al fotograma clave, o NULL si este fotograma clave no depende de otro fotogramas clave.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de un descriptor de acceso a un fotograma clave que depende de este fotograma clave.  
  
##  <a name="getoffset"></a>CKeyFrame::GetOffset  
 Devuelve un desplazamiento de otro fotogramas clave.  
  
```  
UI_ANIMATION_SECONDS GetOffset();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Desplazamiento en segundos desde otro fotograma clave.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a este método para determinar la posición de desplazamiento en segundos desde otro fotograma clave.  
  
##  <a name="gettransition"></a>CKeyFrame::GetTransition  
 Devuelve un puntero a una transición que depende de este fotograma clave.  
  
```  
CBaseTransition* GetTransition();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido para la transición, o NULL si este fotograma clave no depende de la transición.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de un descriptor de acceso a una transición que depende de este fotograma clave.  
  
##  <a name="m_offset"></a>CKeyFrame::m_offset  
 Especifica el desplazamiento de este fotograma clave desde un fotograma clave que se almacena en m_pExistingKeyFrame.  
  
```  
UI_ANIMATION_SECONDS m_offset;  
```  
  
##  <a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame  
 Almacena un puntero a un keframe existente. Este fotograma clave se agrega al guión gráfico con m_offset el fotograma clave existente.  
  
```  
CBaseKeyFrame* m_pExistingKeyFrame;  
```  
  
##  <a name="m_ptransition"></a>CKeyFrame::m_pTransition  
 Almacena un puntero a la transición que comienza en este fotograma clave.  
  
```  
CBaseTransition* m_pTransition;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

