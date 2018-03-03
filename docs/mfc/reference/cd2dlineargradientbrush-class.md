---
title: Clase CD2DLinearGradientBrush | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 19c060c846d8dfd12a8b783f0b01153c9a424cfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dlineargradientbrush-class"></a>Clase CD2DLinearGradientBrush
Un contenedor para ID2D1LinearGradientBrush.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Construye un objeto CD2DLinearGradientBrush.|  
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destructor. Se llama cuando se destruye un objeto de pincel de degradado lineal D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::Attach](#attach)|Adjunta existente de la interfaz de recurso para el objeto|  
|[CD2DLinearGradientBrush::Create](#create)|Crea un CD2DLinearGradientBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DLinearGradientBrush::Destroy](#destroy)|Destruye un objeto CD2DLinearGradientBrush. (Invalida [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|  
|[CD2DLinearGradientBrush::Detach](#detach)|Separa la interfaz de recurso del objeto|  
|[CD2DLinearGradientBrush::Get](#get)|Interfaz de ID2D1LinearGradientBrush devuelve|  
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Recupera las coordenadas finales del degradado lineal|  
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Recupera las coordenadas iniciales del degradado lineal|  
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Establece las coordenadas finales del degradado lineal en el espacio de coordenadas del pincel|  
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Establece las coordenadas iniciales del degradado lineal en el espacio de coordenadas del pincel|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Interfaz de ID2D1LinearGradientBrush devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Los puntos inicial y final del degradado.|  
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Un puntero a un ID2D1LinearGradientBrush.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DLinearGradientBrush`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush  
 Destructor. Se llama cuando se destruye un objeto de pincel de degradado lineal D2D.  
  
```  
virtual ~CD2DLinearGradientBrush();
```  
  
##  <a name="attach"></a>CD2DLinearGradientBrush::Attach  
 Adjunta existente de la interfaz de recurso para el objeto  
  
```  
void Attach(ID2D1LinearGradientBrush* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush  
 Construye un objeto CD2DLinearGradientBrush.  
  
```  
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,  
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,  
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Un puntero para el destino de representación.  
  
 `gradientStops`  
 Un puntero a una matriz de estructuras D2D1_GRADIENT_STOP.  
  
 `gradientStopsCount`  
 Un valor mayor o igual a 1 que especifica el número de puntos de degradado de la matriz gradientStops.  
  
 `LinearGradientBrushProperties`  
 Los puntos inicial y final del degradado.  
  
 `colorInterpolationGamma`  
 El espacio en el color que se realiza una interpolación entre los delimitadores de degradado.  
  
 `extendMode`  
 El comportamiento del degradado que se encuentra fuera del intervalo [0,1] normalizado.  
  
 `pBrushProperties`  
 Un puntero a la opacidad y la transformación de un pincel.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="create"></a>CD2DLinearGradientBrush::Create  
 Crea un CD2DLinearGradientBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Un puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DLinearGradientBrush::Destroy  
 Destruye un objeto CD2DLinearGradientBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DLinearGradientBrush::Detach  
 Separa la interfaz de recurso del objeto  
  
```  
ID2D1LinearGradientBrush* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz recursos separados.  
  
##  <a name="get"></a>CD2DLinearGradientBrush::Get  
 Interfaz de ID2D1LinearGradientBrush devuelve  
  
```  
ID2D1LinearGradientBrush* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1LinearGradientBrush o NULL si el objeto todavía no está inicializado.  
  
##  <a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint  
 Recupera las coordenadas finales del degradado lineal  
  
```  
CD2DPointF GetEndPoint() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las coordenadas bidimensionales finales del degradado lineal, en el espacio de coordenadas del pincel  
  
##  <a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint  
 Recupera las coordenadas iniciales del degradado lineal  
  
```  
CD2DPointF GetStartPoint() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las coordenadas bidimensionales iniciales del degradado lineal, en el espacio de coordenadas del pincel  
  
##  <a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties  
 Los puntos inicial y final del degradado.  
  
```  
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;  
```  
  
##  <a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush  
 Un puntero a un ID2D1LinearGradientBrush.  
  
```  
ID2D1LinearGradientBrush* m_pLinearGradientBrush;  
```  
  
##  <a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *  
 Interfaz de ID2D1LinearGradientBrush devuelve  
  
```  
operator ID2D1LinearGradientBrush*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1LinearGradientBrush o NULL si el objeto todavía no está inicializado.  
  
##  <a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint  
 Establece las coordenadas finales del degradado lineal en el espacio de coordenadas del pincel  
  
```  
void SetEndPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Las coordenadas bidimensionales finales del degradado lineal, en el espacio de coordenadas del pincel  
  
##  <a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint  
 Establece las coordenadas iniciales del degradado lineal en el espacio de coordenadas del pincel  
  
```  
void SetStartPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Las coordenadas bidimensionales iniciales del degradado lineal, en el espacio de coordenadas del pincel  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
