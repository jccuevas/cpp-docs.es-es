---
title: Clase CD2DResource | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CD2DResource
- CD2DResource
dev_langs:
- C++
helpviewer_keywords:
- CD2DResource class
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
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
ms.openlocfilehash: b5a357a3653e2126de85b21efddca881c6c43a09
ms.lasthandoff: 02/24/2017

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
  
##  <a name="a-namedtorcd2dresourcea--cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a>CD2DResource:: ~ CD2DResource  
 Destructor. Se llama cuando se destruye un objeto de recurso de D2D.  
  
```  
virtual ~CD2DResource();
```  
  
##  <a name="a-namecd2dresourcea--cd2dresourcecd2dresource"></a><a name="cd2dresource"></a>CD2DResource::CD2DResource  
 Construye un objeto CD2DResource.  
  
```  
CD2DResource(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="a-namecreatea--cd2dresourcecreate"></a><a name="create"></a>CD2DResource::Create  
 Crea un CD2DResource.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="a-namedestroya--cd2dresourcedestroy"></a><a name="destroy"></a>CD2DResource::Destroy  
 Destruye un objeto CD2DResource.  
  
```  
virtual void Destroy() = 0;  
```  
  
##  <a name="a-nameisautodestroya--cd2dresourceisautodestroy"></a><a name="isautodestroy"></a>CD2DResource::IsAutoDestroy  
 Comprobación automática destruir marca.  
  
```  
BOOL IsAutoDestroy() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el objeto se destruirá por su propietario; de lo contrario, FALSE.  
  
##  <a name="a-nameisvalida--cd2dresourceisvalid"></a><a name="isvalid"></a>CD2DResource::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
virtual BOOL IsValid() const = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válido; de lo contrario, FALSE.  
  
##  <a name="a-namembisautodestroya--cd2dresourcembisautodestroy"></a><a name="m_bisautodestroy"></a>CD2DResource::m_bIsAutoDestroy  
 Recurso será destoyed propietario (CRenderTarget)  
  
```  
BOOL m_bIsAutoDestroy;  
```  
  
##  <a name="a-namempparenttargeta--cd2dresourcempparenttarget"></a><a name="m_pparenttarget"></a>CD2DResource::m_pParentTarget  
 Puntero al elemento primario CRenderTarget)  
  
```  
CRenderTarget* m_pParentTarget;  
```  
  
##  <a name="a-namerecreatea--cd2dresourcerecreate"></a><a name="recreate"></a>CD2DResource::ReCreate  
 Vuelve a crear un CD2DResource.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Puntero para el destino de representación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

