---
title: Clase CD2DBitmapBrush | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmapBrush class
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a9ab15dcae8715b98cc9f723a710b64e83649bf9
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dbitmapbrush-class"></a>Clase CD2DBitmapBrush
Un contenedor para ID2D1BitmapBrush.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Sobrecargado. Construye un objeto CD2DBitmapBrush de archivo.|  
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|Destructor. Se llama cuando se destruye un objeto brush de mapa de bits de D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DBitmapBrush::Create](#create)|Crea un CD2DBitmapBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmapBrush::Destroy](#destroy)|Destruye un objeto CD2DBitmapBrush. (Invalida [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|  
|[CD2DBitmapBrush::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DBitmapBrush::Get](#get)|Interfaz de ID2D1BitmapBrush devuelve|  
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Obtiene el origen del mapa de bits que usa este pincel para pintar|  
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Obtiene el método por el que el pincel de mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Obtiene el método por el que el pincel de mosaico verticalmente las áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Obtiene el método de interpolación que se utiliza cuando el mapa de bits de pincel se escala o girada|  
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Especifica el origen del mapa de bits que usa este pincel para pintar|  
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Especifica cómo el pincel de mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Especifica cómo el pincel de mosaico verticalmente las áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Especifica el modo de interpolación que se utiliza cuando el mapa de bits de pincel se escala o girada|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicializa el objeto|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Interfaz de ID2D1BitmapBrush devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Almacena un puntero a un objeto CD2DBitmap.|  
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Almacena un puntero a un objeto ID2D1BitmapBrush.|  
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Propiedades del pincel de mapa de bits.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DBitmapBrush`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="dtor"></a>CD2DBitmapBrush:: ~ CD2DBitmapBrush  
 Destructor. Se llama cuando se destruye un objeto brush de mapa de bits de D2D.  
  
```  
virtual ~CD2DBitmapBrush();
```  
  
##  <a name="attach"></a>CD2DBitmapBrush::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1BitmapBrush* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush  
 Construye un objeto CD2DBitmapBrush.  
  
```  
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszImagePath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `pBitmapBrushProperties`  
 Un puntero a los modos de ampliación y el modo de interpolación de un pincel de mapa de bits.  
  
 `pBrushProperties`  
 Puntero a la opacidad y la transformación de un pincel.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
 `uiResID`  
 El número de Id. de recurso del recurso.  
  
 `lpszType`  
 Puntero a una cadena terminada en null que contiene el tipo de recurso.  
  
 `sizeDest`  
 Tamaño de destino del mapa de bits.  
  
 `lpszImagePath`  
 Puntero a una cadena terminada en null que contiene el nombre del archivo.  
  
##  <a name="commoninit"></a>CD2DBitmapBrush::CommonInit  
 Inicializa el objeto  
  
```  
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitmapBrushProperties`  
 Puntero a las propiedades de pincel de mapa de bits.  
  
##  <a name="create"></a>CD2DBitmapBrush::Create  
 Crea un CD2DBitmapBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DBitmapBrush::Destroy  
 Destruye un objeto CD2DBitmapBrush.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DBitmapBrush::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1BitmapBrush* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="get"></a>CD2DBitmapBrush::Get  
 Interfaz de ID2D1BitmapBrush devuelve  
  
```  
ID2D1BitmapBrush* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1BitmapBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap  
 Obtiene el origen del mapa de bits que usa este pincel para pintar  
  
```  
CD2DBitmap* GetBitmap();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un objeto CD2DBitmap o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX  
 Obtiene el método por el que el pincel de mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits  
  
```  
D2D1_EXTEND_MODE GetExtendModeX() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que especifica cómo el pincel de mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits  
  
##  <a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY  
 Obtiene el método por el que el pincel de mosaico verticalmente las áreas que se extienden más allá de su mapa de bits  
  
```  
D2D1_EXTEND_MODE GetExtendModeY() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que especifica cómo el pincel de mosaico verticalmente las áreas que se extienden más allá de su mapa de bits  
  
##  <a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode  
 Obtiene el método de interpolación que se utiliza cuando el mapa de bits de pincel se escala o girada  
  
```  
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método de interpolación que se utiliza cuando el mapa de bits de pincel se escala o girada  
  
##  <a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap  
 Almacena un puntero a un objeto CD2DBitmap.  
  
```  
CD2DBitmap* m_pBitmap;  
```  
  
##  <a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush  
 Almacena un puntero a un objeto ID2D1BitmapBrush.  
  
```  
ID2D1BitmapBrush* m_pBitmapBrush;  
```  
  
##  <a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties  
 Propiedades del pincel de mapa de bits.  
  
```  
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;  
```  
  
##  <a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::operator ID2D1BitmapBrush *  
 Interfaz de ID2D1BitmapBrush devuelve  
  
```  
operator ID2D1BitmapBrush*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1BitmapBrush o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap  
 Especifica el origen del mapa de bits que usa este pincel para pintar  
  
```  
void SetBitmap(CD2DBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitmap`  
 El origen de mapa de bits que se usa el pincel  
  
##  <a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX  
 Especifica cómo el pincel de mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits  
  
```  
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```  
  
### <a name="parameters"></a>Parámetros  
 `extendModeX`  
 Un valor que especifica cómo el pincel de mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits  
  
##  <a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY  
 Especifica cómo el pincel de mosaico verticalmente las áreas que se extienden más allá de su mapa de bits  
  
```  
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```  
  
### <a name="parameters"></a>Parámetros  
 `extendModeY`  
 Un valor que especifica cómo el pincel de mosaico verticalmente las áreas que se extienden más allá de su mapa de bits  
  
##  <a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode  
 Especifica el modo de interpolación que se utiliza cuando el mapa de bits de pincel se escala o girada  
  
```  
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `interpolationMode`  
 El modo de interpolación que se utiliza cuando el mapa de bits de pincel se escala o girada  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

