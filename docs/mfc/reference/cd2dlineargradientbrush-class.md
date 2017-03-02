---
title: Clase CD2DLinearGradientBrush | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CD2DLinearGradientBrush
- CD2DLinearGradientBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DLinearGradientBrush class
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
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
ms.openlocfilehash: dd288478a751d921cc4d9fcd9433e391275cee66
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dlineargradientbrush-class"></a>Clase CD2DLinearGradientBrush
Un contenedor para ID2D1LinearGradientBrush.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Construye un objeto CD2DLinearGradientBrush.|  
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destructor. Se llama cuando se destruye un objeto de pincel de degradado lineal D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DLinearGradientBrush::Create](#create)|Crea un CD2DLinearGradientBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DLinearGradientBrush::Destroy](#destroy)|Destruye un objeto CD2DLinearGradientBrush. (Invalida [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|  
|[CD2DLinearGradientBrush::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DLinearGradientBrush::Get](#get)|Interfaz de ID2D1LinearGradientBrush devuelve|  
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Recupera las coordenadas finales del degradado lineal|  
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Recupera las coordenadas iniciales del degradado lineal|  
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Establece las coordenadas finales del degradado lineal en el espacio de coordenadas del pincel|  
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Establece las coordenadas iniciales del degradado lineal en el espacio de coordenadas del pincel|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Interfaz de ID2D1LinearGradientBrush devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Los puntos inicial y final del degradado.|  
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Puntero a un ID2D1LinearGradientBrush.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DLinearGradientBrush`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="a-namedtorcd2dlineargradientbrusha--cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush  
 Destructor. Se llama cuando se destruye un objeto de pincel de degradado lineal D2D.  
  
```  
virtual ~CD2DLinearGradientBrush();
```  
  
##  <a name="a-nameattacha--cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2DLinearGradientBrush::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1LinearGradientBrush* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="a-namecd2dlineargradientbrusha--cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush  
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
 Puntero para el destino de representación.  
  
 `gradientStops`  
 Puntero a una matriz de estructuras D2D1_GRADIENT_STOP.  
  
 `gradientStopsCount`  
 Un valor mayor o igual a 1 que especifica el número de puntos de degradado en la matriz gradientStops.  
  
 `LinearGradientBrushProperties`  
 Los puntos inicial y final del degradado.  
  
 `colorInterpolationGamma`  
 El espacio en el color que se realiza la interpolación entre los delimitadores de degradado.  
  
 `extendMode`  
 El comportamiento del degradado fuera del intervalo [0,1] normalizado.  
  
 `pBrushProperties`  
 Puntero a la opacidad y la transformación de un pincel.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="a-namecreatea--cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2DLinearGradientBrush::Create  
 Crea un CD2DLinearGradientBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="a-namedestroya--cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2DLinearGradientBrush::Destroy  
 Destruye un objeto CD2DLinearGradientBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="a-namedetacha--cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2DLinearGradientBrush::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1LinearGradientBrush* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="a-namegeta--cd2dlineargradientbrushget"></a><a name="get"></a>CD2DLinearGradientBrush::Get  
 Interfaz de ID2D1LinearGradientBrush devuelve  
  
```  
ID2D1LinearGradientBrush* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1LinearGradientBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="a-namegetendpointa--cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint  
 Recupera las coordenadas finales del degradado lineal  
  
```  
CD2DPointF GetEndPoint() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Coordenadas bidimensionales finales del degradado lineal, en el espacio de coordenadas del pincel  
  
##  <a name="a-namegetstartpointa--cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint  
 Recupera las coordenadas iniciales del degradado lineal  
  
```  
CD2DPointF GetStartPoint() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las coordenadas bidimensionales iniciales del degradado lineal, en el espacio de coordenadas del pincel  
  
##  <a name="a-namemlineargradientbrushpropertiesa--cd2dlineargradientbrushmlineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties  
 Los puntos inicial y final del degradado.  
  
```  
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;  
```  
  
##  <a name="a-namemplineargradientbrusha--cd2dlineargradientbrushmplineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush  
 Puntero a un ID2D1LinearGradientBrush.  
  
```  
ID2D1LinearGradientBrush* m_pLinearGradientBrush;  
```  
  
##  <a name="a-nameoperatorid2d1lineargradientbrushstara--cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *  
 Interfaz de ID2D1LinearGradientBrush devuelve  
  
```  
operator ID2D1LinearGradientBrush*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1LinearGradientBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="a-namesetendpointa--cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint  
 Establece las coordenadas finales del degradado lineal en el espacio de coordenadas del pincel  
  
```  
void SetEndPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Coordenadas bidimensionales finales del degradado lineal, en el espacio de coordenadas del pincel  
  
##  <a name="a-namesetstartpointa--cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint  
 Establece las coordenadas iniciales del degradado lineal en el espacio de coordenadas del pincel  
  
```  
void SetStartPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Las coordenadas bidimensionales iniciales del degradado lineal, en el espacio de coordenadas del pincel  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

