---
title: Clase CHwndRenderTarget | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CHwndRenderTarget class
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
caps.latest.revision: 17
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
ms.openlocfilehash: 1af6795e89c995ba6b5a7b094f06b0aea776f561
ms.lasthandoff: 02/24/2017

---
# <a name="chwndrendertarget-class"></a>Clase CHwndRenderTarget
Un contenedor para ID2D1HwndRenderTarget.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Construye un objeto CHwndRenderTarget de HWND.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::Attach](#attach)|Conexiones existentes representan la interfaz de destino para el objeto|  
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Indica si está ocluido HWND asociado a este destino de representación.|  
|[CHwndRenderTarget::Create](#create)|Crea un destino de representación asociado a la ventana|  
|[CHwndRenderTarget::Detach](#detach)|Separa la interfaz de destino de representación del objeto|  
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Devuelve el HWND asociado a este destino de representación.|  
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Interfaz de ID2D1HwndRenderTarget devuelve.|  
|[CHwndRenderTarget::ReCreate](#recreate)|Vuelve a crear un destino de representación asociado a la ventana|  
|[CHwndRenderTarget::Resize](#resize)|Cambia el tamaño de destino de representación para el tamaño de píxel especificado|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|Interfaz de ID2D1HwndRenderTarget devuelve.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Un puntero a un objeto ID2D1HwndRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="attach"></a>CHwndRenderTarget::Attach  
 Conexiones existentes representan la interfaz de destino para el objeto  
  
```  
void Attach(ID2D1HwndRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTarget`  
 Interfaz existente del destino de representación. No puede ser NULL  
  
##  <a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState  
 Indica si está ocluido HWND asociado a este destino de representación.  
  
```  
D2D1_WINDOW_STATE CheckWindowState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indica si el HWND asociado a este destino de representación está ocluido.  
  
##  <a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget  
 Construye un objeto CHwndRenderTarget de HWND.  
  
```  
CHwndRenderTarget(HWND hwnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `hwnd`  
 HWND asociado a este destino de representación  
  
##  <a name="create"></a>CHwndRenderTarget::Create  
 Crea un destino de representación asociado a la ventana  
  
```  
BOOL Create(HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 HWND asociado a este destino de representación  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE  
  
##  <a name="detach"></a>CHwndRenderTarget::Detach  
 Separa la interfaz de destino de representación del objeto  
  
```  
ID2D1HwndRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al desasociar representar la interfaz de destino.  
  
##  <a name="gethwnd"></a>CHwndRenderTarget::GetHwnd  
 Devuelve el HWND asociado a este destino de representación.  
  
```  
HWND GetHwnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 HWND asociado a este destino de representación.  
  
##  <a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget  
 Interfaz de ID2D1HwndRenderTarget devuelve.  
  
```  
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1HwndRenderTarget o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget  
 Un puntero a un objeto ID2D1HwndRenderTarget.  
  
```  
ID2D1HwndRenderTarget* m_pHwndRenderTarget;  
```  
  
##  <a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::operator ID2D1HwndRenderTarget *  
 Interfaz de ID2D1HwndRenderTarget devuelve.  
  
```  
operator ID2D1HwndRenderTarget*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1HwndRenderTarget o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="recreate"></a>CHwndRenderTarget::ReCreate  
 Vuelve a crear un destino de representación asociado a la ventana  
  
```  
BOOL ReCreate(HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 HWND asociado a este destino de representación  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="resize"></a>CHwndRenderTarget::Resize  
 Cambia el tamaño de destino de representación para el tamaño de píxel especificado  
  
```  
BOOL Resize(const CD2DSizeU& size);
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 El nuevo tamaño del destino de representación en píxeles del dispositivo  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

