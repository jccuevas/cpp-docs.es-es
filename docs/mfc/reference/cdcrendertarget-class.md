---
title: Clase CDCRenderTarget | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CDCRenderTarget
- CDCRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CDCRenderTarget class
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2bbd62b06f4287904fce49f8a6ce9900476b07c0
ms.lasthandoff: 02/24/2017

---
# <a name="cdcrendertarget-class"></a>Clase CDCRenderTarget
Un contenedor para ID2D1DCRenderTarget.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Construye un objeto CDCRenderTarget.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](#attach)|Conexiones existentes representan la interfaz de destino para el objeto|  
|[CDCRenderTarget::BindDC](#binddc)|El destino de representación se enlaza al contexto de dispositivo que emite los comandos de dibujo|  
|[CDCRenderTarget::Create](#create)|Crea un CDCRenderTarget.|  
|[CDCRenderTarget::Detach](#detach)|Separa la interfaz de destino de representación del objeto|  
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Interfaz de ID2D1DCRenderTarget devuelve|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Interfaz de ID2D1DCRenderTarget devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Un puntero a un objeto ID2D1DCRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="a-nameattacha--cdcrendertargetattach"></a><a name="attach"></a>CDCRenderTarget::Attach  
 Conexiones existentes representan la interfaz de destino para el objeto  
  
```  
void Attach(ID2D1DCRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTarget`  
 Interfaz existente del destino de representación. No puede ser NULL  
  
##  <a name="a-namebinddca--cdcrendertargetbinddc"></a><a name="binddc"></a>CDCRenderTarget::BindDC  
 El destino de representación se enlaza al contexto de dispositivo que emite los comandos de dibujo  
  
```  
BOOL BindDC(
    const CDC& dc,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `dc`  
 El contexto de dispositivo para que el destino de representación emite comandos de dibujo  
  
 `rect`  
 Las dimensiones del identificador de un contexto de dispositivo (HDC) al que está enlazado el destino de representación  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="a-namecdcrendertargeta--cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget  
 Construye un objeto CDCRenderTarget.  
  
```  
CDCRenderTarget();
```  
  
##  <a name="a-namecreatea--cdcrendertargetcreate"></a><a name="create"></a>CDCRenderTarget::Create  
 Crea un CDCRenderTarget.  
  
```  
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```  
  
### <a name="parameters"></a>Parámetros  
 `props`  
 El modo de representación, formato de píxel, opciones de comunicación remota, información de PPP y el soporte de DirectX mínimo necesario para la representación de hardware.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.  
  
##  <a name="a-namedetacha--cdcrendertargetdetach"></a><a name="detach"></a>CDCRenderTarget::Detach  
 Separa la interfaz de destino de representación del objeto  
  
```  
ID2D1DCRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al desasociar representar la interfaz de destino.  
  
##  <a name="a-namegetdcrendertargeta--cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget  
 Interfaz de ID2D1DCRenderTarget devuelve  
  
```  
ID2D1DCRenderTarget* GetDCRenderTarget();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="a-namempdcrendertargeta--cdcrendertargetmpdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget  
 Un puntero a un objeto ID2D1DCRenderTarget.  
  
```  
ID2D1DCRenderTarget* m_pDCRenderTarget;  
```  
  
##  <a name="a-nameoperatorid2d1dcrendertargetstara--cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operator ID2D1DCRenderTarget *  
 Interfaz de ID2D1DCRenderTarget devuelve  
  
```  
operator ID2D1DCRenderTarget*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto no se ha inicializado todavía.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

