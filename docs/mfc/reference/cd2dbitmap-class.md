---
title: Clase CD2DBitmap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmap class
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
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
ms.openlocfilehash: f88a6376069c07c61311d74faca104e821a259bd
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dbitmap-class"></a>Clase CD2DBitmap
Un contenedor para ID2D1Bitmap.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DBitmap : public CD2DResource;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Sobrecargado. Construye un objeto CD2DBitmap de HBITMAP.|  
|[CD2DBitmap:: ~ CD2DBitmap](#_dtorcd2dbitmap)|Destructor. Se llama cuando se destruye un objeto de mapa de bits de D2D.|  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Sobrecargado. Construye un objeto CD2DBitmap.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::Attach](#attach)|Conexiones existentes de la interfaz de recursos para el objeto|  
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Copia la región especificada del mapa de bits especificado en el mapa de bits actual|  
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Copia la región especificada de la memoria en el mapa de bits actual|  
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Copias de la región especificada desde el destino de representación en el mapa de bits actual|  
|[CD2DBitmap::Create](#create)|Crea un CD2DBitmap. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmap::Destroy](#destroy)|Destruye un objeto CD2DBitmap. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DBitmap::Detach](#detach)|Separa la interfaz de recursos desde el objeto|  
|[CD2DBitmap::Get](#get)|Interfaz de ID2D1Bitmap devuelve|  
|[CD2DBitmap::GetDPI](#getdpi)|Devolver los puntos por pulgada (PPP) del mapa de bits|  
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Recupera el modo alfa y el formato de píxel del mapa de bits|  
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Devuelve el tamaño, en unidades de dependiente del dispositivo (píxeles), del mapa de bits|  
|[CD2DBitmap::GetSize](#getsize)|Devuelve el tamaño, en píxeles independientes del dispositivo (DIP), del mapa de bits|  
|[CD2DBitmap::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::CommonInit](#commoninit)|Inicializa el objeto|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Interfaz de ID2D1Bitmap devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUE si se debe destruir m_hBmpSrc; de lo contrario, FALSE.|  
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Identificador del mapa de bits de origen.|  
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Tipo de recurso.|  
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Almacena un puntero a un objeto ID2D1Bitmap.|  
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Tamaño de destino del mapa de bits.|  
|[CD2DBitmap::m_strPath](#m_strpath)|Ruta de acceso de archivo Botmap.|  
|[CD2DBitmap::m_uiResID](#m_uiresid)|Identificador de recurso de mapa de bits.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DBitmap`
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dbitmap"></a>CD2DBitmap:: ~ CD2DBitmap  
 Destructor. Se llama cuando se destruye un objeto de mapa de bits de D2D.  
  
```  
virtual ~CD2DBitmap();
```  
  
##  <a name="attach"></a>CD2DBitmap::Attach  
 Conexiones existentes de la interfaz de recursos para el objeto  
  
```  
void Attach(ID2D1Bitmap* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Interfaz de recursos existente. No puede ser NULL  
  
##  <a name="cd2dbitmap"></a>CD2DBitmap::CD2DBitmap  
 Construye un objeto CD2DBitmap de recurso.  
  
```  
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszPath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    HBITMAP hbmpSrc,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `uiResID`  
 El número de Id. de recurso del recurso.  
  
 `lpszType`  
 Puntero a una cadena terminada en null que contiene el tipo de recurso.  
  
 `sizeDest`  
 Tamaño de destino del mapa de bits.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
 `lpszPath`  
 Puntero a una cadena terminada en null que contiene el nombre del archivo.  
  
 `hbmpSrc`  
 Identificador del mapa de bits.  
  
##  <a name="commoninit"></a>CD2DBitmap::CommonInit  
 Inicializa el objeto  
  
```  
void CommonInit();
```  
  
##  <a name="copyfrombitmap"></a>CD2DBitmap::CopyFromBitmap  
 Copia la región especificada del mapa de bits especificado en el mapa de bits actual  
  
```  
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitmap`  
 Copiar desde el mapa de bits  
  
 `destPoint`  
 En el mapa de bits actual, se copia la esquina superior izquierda del área a la que la región especificada por srcRect  
  
 `srcRect`  
 El área de mapa de bits para copiar  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="copyfrommemory"></a>CD2DBitmap::CopyFromMemory  
 Copia la región especificada de la memoria en el mapa de bits actual  
  
```  
HRESULT CopyFromMemory(
    const void* srcData,  
    UINT32 pitch,  
    const CD2DRectU* destRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `srcData`  
 Los datos que se va a copiar  
  
 `pitch`  
 Stride o tono del mapa de bits de origen almacenado en srcData. El paso es el número de bytes de una línea de exploración (una fila de píxeles en memoria). El intervalo se puede calcular de la siguiente fórmula: ancho de píxel * bytes por píxel + relleno de memoria  
  
 `destRect`  
 En el mapa de bits actual, se copia la esquina superior izquierda del área a la que la región especificada por srcRect  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="copyfromrendertarget"></a>CD2DBitmap::CopyFromRenderTarget  
 Copias de la región especificada desde el destino de representación en el mapa de bits actual  
  
```  
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 El destino de representación que contiene el área para copiar  
  
 `destPoint`  
 En el mapa de bits actual, se copia la esquina superior izquierda del área a la que la región especificada por srcRect  
  
 `srcRect`  
 El área de renderTarget para copiar  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="create"></a>CD2DBitmap::Create  
 Crea un CD2DBitmap.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DBitmap::Destroy  
 Destruye un objeto CD2DBitmap.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DBitmap::Detach  
 Separa la interfaz de recursos desde el objeto  
  
```  
ID2D1Bitmap* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a interfaz desasociadas recursos.  
  
##  <a name="get"></a>CD2DBitmap::Get  
 Interfaz de ID2D1Bitmap devuelve  
  
```  
ID2D1Bitmap* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1Bitmap o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="getdpi"></a>CD2DBitmap::GetDPI  
 Devolver los puntos por pulgada (PPP) del mapa de bits  
  
```  
CD2DSizeF GetDPI() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de PPP horizontal y vertical del mapa de bits.  
  
##  <a name="getpixelformat"></a>CD2DBitmap::GetPixelFormat  
 Recupera el modo alfa y el formato de píxel del mapa de bits  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Píxel alfa y formato de modo de mapa de bits.  
  
##  <a name="getpixelsize"></a>CD2DBitmap::GetPixelSize  
 Devuelve el tamaño, en unidades de dependiente del dispositivo (píxeles), del mapa de bits  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño, en píxeles, del mapa de bits...  
  
##  <a name="getsize"></a>CD2DBitmap::GetSize  
 Devuelve el tamaño, en píxeles independientes del dispositivo (DIP), del mapa de bits  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño, en DIP del mapa de bits.  
  
##  <a name="isvalid"></a>CD2DBitmap::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válido; de lo contrario, FALSE.  
  
##  <a name="m_bautodestroyhbmp"></a>CD2DBitmap::m_bAutoDestroyHBMP  
 TRUE si se debe destruir m_hBmpSrc; de lo contrario, FALSE.  
  
```  
BOOL m_bAutoDestroyHBMP;  
```  
  
##  <a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc  
 Identificador del mapa de bits de origen.  
  
```  
HBITMAP m_hBmpSrc;  
```  
  
##  <a name="m_lpsztype"></a>CD2DBitmap::m_lpszType  
 Tipo de recurso.  
  
```  
LPCTSTR m_lpszType;  
```  
  
##  <a name="m_pbitmap"></a>CD2DBitmap::m_pBitmap  
 Almacena un puntero a un objeto ID2D1Bitmap.  
  
```  
ID2D1Bitmap* m_pBitmap;  
```  
  
##  <a name="m_sizedest"></a>CD2DBitmap::m_sizeDest  
 Tamaño de destino del mapa de bits.  
  
```  
CD2DSizeU m_sizeDest;  
```  
  
##  <a name="m_strpath"></a>CD2DBitmap::m_strPath  
 Ruta de acceso de archivo Botmap.  
  
```  
CString m_strPath;  
```  
  
##  <a name="m_uiresid"></a>CD2DBitmap::m_uiResID  
 Identificador de recurso de mapa de bits.  
  
```  
UINT m_uiResID;  
```  
  
##  <a name="operator_id2d1bitmap_star"></a>CD2DBitmap::operator ID2D1Bitmap *  
 Interfaz de ID2D1Bitmap devuelve  
  
```  
operator ID2D1Bitmap*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1Bitmap o NULL si el objeto no se ha inicializado todavía.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

