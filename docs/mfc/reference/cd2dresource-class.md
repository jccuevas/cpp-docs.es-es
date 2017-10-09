---
title: Clase CD2DResource | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
dev_langs:
- C++
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: b292bf680a146d730554c56c60df9a649b670ba3
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="cd2dresource-class"></a>Clase CD2DResource
Una clase abstracta que proporciona una interfaz para crear y administrar recursos de D2D como pinceles, capas y textos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DResource : public CObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DResource::CD2DResource](#cd2dresource)|Construye un objeto CD2DResource.|  
|[CD2DResource:: ~ CD2DResource](#cd2dresource__~cd2dresource)|Destructor. Se llama cuando se destruye un objeto de recurso de D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DResource::Create](#create)|Crea un CD2DResource.|  
|[CD2DResource::Destroy](#destroy)|Destruye un objeto CD2DResource.|  
|[CD2DResource::IsValid](#isvalid)|Comprobaciones de validez de los recursos|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Comprobación automática destruir marca.|  
|[CD2DResource::ReCreate](#recreate)|Vuelve a crear un CD2DResource.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Recurso será destoyed propietario (CRenderTarget)|  
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Puntero al elemento primario CRenderTarget)|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CD2DResource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dresource"></a>CD2DResource:: ~ CD2DResource  
 Destructor. Se llama cuando se destruye un objeto de recurso de D2D.  
  
```  
virtual ~CD2DResource();
```  
  
##  <a name="cd2dresource"></a>CD2DResource::CD2DResource  
 Construye un objeto CD2DResource.  
  
```  
CD2DResource(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Un puntero para el destino de representación.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="create"></a>CD2DResource::Create  
 Crea un CD2DResource.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Un puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DResource::Destroy  
 Destruye un objeto CD2DResource.  
  
```  
virtual void Destroy() = 0;  
```  
  
##  <a name="isautodestroy"></a>CD2DResource::IsAutoDestroy  
 Comprobación automática destruir marca.  
  
```  
BOOL IsAutoDestroy() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el objeto se destruirá el propietario; en caso contrario, FALSE.  
  
##  <a name="isvalid"></a>CD2DResource::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
virtual BOOL IsValid() const = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válida; en caso contrario, FALSE.  
  
##  <a name="m_bisautodestroy"></a>CD2DResource::m_bIsAutoDestroy  
 Recurso será destoyed propietario (CRenderTarget)  
  
```  
BOOL m_bIsAutoDestroy;  
```  
  
##  <a name="m_pparenttarget"></a>CD2DResource::m_pParentTarget  
 Puntero al elemento primario CRenderTarget)  
  
```  
CRenderTarget* m_pParentTarget;  
```  
  
##  <a name="recreate"></a>CD2DResource::ReCreate  
 Vuelve a crear un CD2DResource.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Un puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

