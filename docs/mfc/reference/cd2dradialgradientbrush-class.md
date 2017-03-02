---
title: Clase CD2DRadialGradientBrush | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRadialGradientBrush
- afxrendertarget/CD2DRadialGradientBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DRadialGradientBrush class
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
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
ms.openlocfilehash: 8b3fd7f468745567969ba1f7e9d6871a9060582b
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dradialgradientbrush-class"></a>Clase CD2DRadialGradientBrush
Un contenedor para ID2D1RadialGradientBrush.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Construye un objeto CD2DLinearGradientBrush.|  
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destructor. Se llama cuando se destruye un objeto de pincel de degradado radial D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DRadialGradientBrush::Create](#create)|Crea un CD2DRadialGradientBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DRadialGradientBrush::Destroy](#destroy)|Destruye un objeto CD2DRadialGradientBrush. (Invalida [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|  
|[CD2DRadialGradientBrush::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DRadialGradientBrush::Get](#get)|Interfaz de ID2D1RadialGradientBrush devuelve|  
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Recupera el centro de la elipse de degradado|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Recupera el desplazamiento del origen del degradado con respecto al centro de la elipse de degradado|  
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Recupera el radio x de la elipse de degradado|  
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Recupera el radio y de la elipse de degradado|  
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Especifica el centro de la elipse del degradado en el espacio de coordenadas del pincel|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Especifica el desplazamiento del origen del degradado con respecto al centro de la elipse de degradado|  
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Especifica el radio x de la elipse del degradado, en el espacio de coordenadas del pincel|  
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Especifica el radio de la elipse del degradado, y en el espacio de coordenadas del pincel|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|Interfaz de ID2D1RadialGradientBrush devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Puntero a un ID2D1RadialGradientBrush.|  
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|El centro, desplazamiento de degradado de origen y radio x y radio y del pincel de degradado del.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DRadialGradientBrush`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="a-namedtorcd2dradialgradientbrusha--cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush  
 Destructor. Se llama cuando se destruye un objeto de pincel de degradado radial D2D.  
  
```  
virtual ~CD2DRadialGradientBrush();
```  
  
##  <a name="a-nameattacha--cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2DRadialGradientBrush::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1RadialGradientBrush* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="a-namecd2dradialgradientbrusha--cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush  
 Construye un objeto CD2DLinearGradientBrush.  
  
```  
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,  
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
  
 `RadialGradientBrushProperties`  
 El centro, desplazamiento de degradado de origen y radio x y radio y del pincel de degradado del.  
  
 `colorInterpolationGamma`  
 El espacio en el color que se realiza la interpolación entre los delimitadores de degradado.  
  
 `extendMode`  
 El comportamiento del degradado fuera del intervalo [0,1] normalizado.  
  
 `pBrushProperties`  
 Puntero a la opacidad y la transformación de un pincel.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="a-namecreatea--cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2DRadialGradientBrush::Create  
 Crea un CD2DRadialGradientBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="a-namedestroya--cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadialGradientBrush::Destroy  
 Destruye un objeto CD2DRadialGradientBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="a-namedetacha--cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadialGradientBrush::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1RadialGradientBrush* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="a-namegeta--cd2dradialgradientbrushget"></a><a name="get"></a>CD2DRadialGradientBrush::Get  
 Interfaz de ID2D1RadialGradientBrush devuelve  
  
```  
ID2D1RadialGradientBrush* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1RadialGradientBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="a-namegetcentera--cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter  
 Recupera el centro de la elipse de degradado  
  
```  
CD2DPointF GetCenter() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El centro de la elipse del degradado. Este valor se expresa en el espacio de coordenadas del pincel  
  
##  <a name="a-namegetgradientoriginoffseta--cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset  
 Recupera el desplazamiento del origen del degradado con respecto al centro de la elipse de degradado  
  
```  
CD2DPointF GetGradientOriginOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El desplazamiento del origen degradado desde el centro de la elipse del degradado. Este valor se expresa en el espacio de coordenadas del pincel  
  
##  <a name="a-namegetradiusxa--cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX  
 Recupera el radio x de la elipse de degradado  
  
```  
FLOAT GetRadiusX() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El radio de x de la elipse del degradado. Este valor se expresa en el espacio de coordenadas del pincel  
  
##  <a name="a-namegetradiusya--cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusY  
 Recupera el radio y de la elipse de degradado  
  
```  
FLOAT GetRadiusY() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Radio y de la elipse del degradado. Este valor se expresa en el espacio de coordenadas del pincel  
  
##  <a name="a-namempradialgradientbrusha--cd2dradialgradientbrushmpradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush  
 Puntero a un ID2D1RadialGradientBrush.  
  
```  
ID2D1RadialGradientBrush* m_pRadialGradientBrush;  
```  
  
##  <a name="a-namemradialgradientbrushpropertiesa--cd2dradialgradientbrushmradialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties  
 El centro, desplazamiento de degradado de origen y radio x y radio y del pincel de degradado del.  
  
```  
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;  
```  
  
##  <a name="a-nameoperatorid2d1radialgradientbrushstara--cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *  
 Interfaz de ID2D1RadialGradientBrush devuelve  
  
```  
operator ID2D1RadialGradientBrush*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1RadialGradientBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="a-namesetcentera--cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter  
 Especifica el centro de la elipse del degradado en el espacio de coordenadas del pincel  
  
```  
void SetCenter(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 El centro de la elipse del degradado, en el espacio de coordenadas del pincel  
  
##  <a name="a-namesetgradientoriginoffseta--cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset  
 Especifica el desplazamiento del origen del degradado con respecto al centro de la elipse de degradado  
  
```  
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 `gradientOriginOffset`  
 El desplazamiento del origen degradado desde el centro de la elipse de degradado  
  
##  <a name="a-namesetradiusxa--cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX  
 Especifica el radio x de la elipse del degradado, en el espacio de coordenadas del pincel  
  
```  
void SetRadiusX(FLOAT radiusX);
```  
  
### <a name="parameters"></a>Parámetros  
 `radiusX`  
 El radio de x de la elipse del degradado. Este valor está en el espacio de coordenadas del pincel  
  
##  <a name="a-namesetradiusya--cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusY  
 Especifica el radio de la elipse del degradado, y en el espacio de coordenadas del pincel  
  
```  
void SetRadiusY(FLOAT radiusY);
```  
  
### <a name="parameters"></a>Parámetros  
 `radiusY`  
 Radio y de la elipse del degradado. Este valor está en el espacio de coordenadas del pincel  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

