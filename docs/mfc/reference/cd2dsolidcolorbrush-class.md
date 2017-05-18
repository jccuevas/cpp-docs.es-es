---
title: Clase CD2DSolidColorBrush | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DSolidColorBrush class
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
caps.latest.revision: 16
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
ms.openlocfilehash: 5b6cbd6a6a5557f5ea23c0556a4b87011b510411
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dsolidcolorbrush-class"></a>Clase CD2DSolidColorBrush
Un contenedor para ID2D1SolidColorBrush.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DSolidColorBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Sobrecargado. Construye un objeto CD2DSolidColorBrush.|  
|[CD2DSolidColorBrush:: ~ CD2DSolidColorBrush](#cd2dsolidcolorbrush__~cd2dsolidcolorbrush)|Destructor. Se llama cuando se destruye un objeto de pincel sólido D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DSolidColorBrush::Create](#create)|Crea un CD2DSolidColorBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DSolidColorBrush::Destroy](#destroy)|Destruye un objeto CD2DSolidColorBrush. (Invalida [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|  
|[CD2DSolidColorBrush::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DSolidColorBrush::Get](#get)|Interfaz de ID2D1SolidColorBrush devuelve|  
|[CD2DSolidColorBrush::GetColor](#getcolor)|Recupera el color de pincel de color sólido|  
|[CD2DSolidColorBrush::SetColor](#setcolor)|Especifica el color de este pincel de color sólido|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|Interfaz de ID2D1SolidColorBrush devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Pincel de color sólido.|  
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Almacena un puntero a un objeto ID2D1SolidColorBrush.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dsolidcolorbrush"></a>CD2DSolidColorBrush:: ~ CD2DSolidColorBrush  
 Destructor. Se llama cuando se destruye un objeto de pincel sólido D2D.  
  
```  
virtual ~CD2DSolidColorBrush();
```  
  
##  <a name="attach"></a>CD2DSolidColorBrush::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1SolidColorBrush* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="cd2dsolidcolorbrush"></a>CD2DSolidColorBrush::CD2DSolidColorBrush  
 Construye un objeto CD2DSolidColorBrush.  
  
```  
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,  
    D2D1_COLOR_F color,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,  
    COLORREF color,  
    int nAlpha = 255,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `color`  
 Los valores de rojos, verde, azul y alfabéticos del color del pincel.  
  
 `pBrushProperties`  
 Puntero a la opacidad y la transformación de un pincel.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
 `nAlpha`  
 La opacidad del color del pincel.  
  
##  <a name="create"></a>CD2DSolidColorBrush::Create  
 Crea un CD2DSolidColorBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DSolidColorBrush::Destroy  
 Destruye un objeto CD2DSolidColorBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DSolidColorBrush::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1SolidColorBrush* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="get"></a>CD2DSolidColorBrush::Get  
 Interfaz de ID2D1SolidColorBrush devuelve  
  
```  
ID2D1SolidColorBrush* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1SolidColorBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="getcolor"></a>CD2DSolidColorBrush::GetColor  
 Recupera el color de pincel de color sólido  
  
```  
D2D1_COLOR_F GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color de este pincel de color sólido  
  
##  <a name="m_colorsolid"></a>CD2DSolidColorBrush::m_colorSolid  
 Pincel de color sólido.  
  
```  
D2D1_COLOR_F m_colorSolid;  
```  
  
##  <a name="m_psolidcolorbrush"></a>CD2DSolidColorBrush::m_pSolidColorBrush  
 Almacena un puntero a un objeto ID2D1SolidColorBrush.  
  
```  
ID2D1SolidColorBrush* m_pSolidColorBrush;  
```  
  
##  <a name="operator_id2d1solidcolorbrush_star"></a>CD2DSolidColorBrush::operator ID2D1SolidColorBrush *  
 Interfaz de ID2D1SolidColorBrush devuelve  
  
```  
operator ID2D1SolidColorBrush*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1SolidColorBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="setcolor"></a>CD2DSolidColorBrush::SetColor  
 Especifica el color de este pincel de color sólido  
  
```  
void SetColor(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>Parámetros  
 `color`  
 El color de este pincel de color sólido  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

