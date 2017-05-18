---
title: Clase CD2DTextLayout | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextLayout class
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
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
ms.openlocfilehash: b9d3873058613041042857b7edf213d207f058c5
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dtextlayout-class"></a>Clase CD2DTextLayout
Un contenedor para IDWriteTextLayout.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Construye un objeto CD2DTextLayout.|  
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|Destructor. Se llama cuando se destruye un objeto de diseño de texto D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::Create](#create)|Crea un CD2DTextLayout. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextLayout::Destroy](#destroy)|Destruye un objeto CD2DTextLayout. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextLayout::Get](#get)|Interfaz de IDWriteTextLayout devuelve|  
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Copia el nombre de familia de fuentes del texto en la posición especificada.|  
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Obtiene el nombre de la configuración regional del texto en la posición especificada.|  
|[CD2DTextLayout::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextLayout::ReCreate](#recreate)|Vuelve a crear un CD2DTextLayout. (Invalida [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Nombre de familia de fuentes terminada en null de conjuntos de texto dentro de un intervalo de texto especificado|  
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Establece el nombre de la configuración regional para el texto dentro de un intervalo de texto especificado|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Interfaz de IDWriteTextLayout devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Puntero a un IDWriteTextLayout.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextlayout"></a>CD2DTextLayout:: ~ CD2DTextLayout  
 Destructor. Se llama cuando se destruye un objeto de diseño de texto D2D.  
  
```  
virtual ~CD2DTextLayout();
```  
  
##  <a name="cd2dtextlayout"></a>CD2DTextLayout::CD2DTextLayout  
 Construye un objeto CD2DTextLayout.  
  
```  
CD2DTextLayout(
    CRenderTarget* pParentTarget,  
    const CString& strText,  
    CD2DTextFormat& textFormat,  
    const CD2DSizeF& sizeMax,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `strText`  
 Un objeto CString que contiene la cadena para crear un nuevo objeto CD2DTextLayout.  
  
 `textFormat`  
 Un objeto CString que contiene el formato que se aplica a la cadena.  
  
 `sizeMax`  
 El tamaño del cuadro de diseño.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="create"></a>CD2DTextLayout::Create  
 Crea un CD2DTextLayout.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="destroy"></a>CD2DTextLayout::Destroy  
 Destruye un objeto CD2DTextLayout.  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>CD2DTextLayout::Get  
 Interfaz de IDWriteTextLayout devuelve  
  
```  
IDWriteTextLayout* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz IDWriteTextLayout o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="getfontfamilyname"></a>CD2DTextLayout::GetFontFamilyName  
 Copia el nombre de familia de fuentes del texto en la posición especificada.  
  
```  
CString GetFontFamilyName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `currentPosition`  
 La posición del texto para examinar.  
  
 `textRange`  
 El intervalo de texto que tiene el mismo formato que el texto en la posición especificada por currentPosition. Esto significa que la ejecución tiene el formato exacto que la posición especificada, incluyendo pero sin limitarse a, el nombre de familia de fuentes.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto CString que contiene el nombre de familia de fuentes actual.  
  
##  <a name="getlocalename"></a>CD2DTextLayout::GetLocaleName  
 Obtiene el nombre de la configuración regional del texto en la posición especificada.  
  
```  
CString GetLocaleName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `currentPosition`  
 La posición del texto que se va a inspeccionar.  
  
 `textRange`  
 El intervalo de texto que tiene el mismo formato que el texto en la posición especificada por currentPosition. Esto significa que la ejecución tiene el formato exacto que la posición especificada, incluyendo pero sin limitarse a, el nombre de la configuración regional.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto CString que contiene el nombre de la configuración regional actual.  
  
##  <a name="isvalid"></a>CD2DTextLayout::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válido; de lo contrario, FALSE.  
  
##  <a name="m_ptextlayout"></a>CD2DTextLayout::m_pTextLayout  
 Puntero a un IDWriteTextLayout.  
  
```  
IDWriteTextLayout* m_pTextLayout;  
```  
  
##  <a name="operator_idwritetextlayout_star"></a>CD2DTextLayout::operator IDWriteTextLayout *  
 Interfaz de IDWriteTextLayout devuelve  
  
```  
operator IDWriteTextLayout*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz IDWriteTextLayout o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="recreate"></a>CD2DTextLayout::ReCreate  
 Vuelve a crear un CD2DTextLayout.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="setfontfamilyname"></a>CD2DTextLayout::SetFontFamilyName  
 Nombre de familia de fuentes terminada en null de conjuntos de texto dentro de un intervalo de texto especificado  
  
```  
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Parámetros  
 `pwzFontFamilyName`  
 El nombre de familia de fuentes que se aplica a la cadena de texto completo dentro del intervalo especificado por textRange  
  
 `textRange`  
 Intervalo de texto al que se aplica este cambio  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE  
  
##  <a name="setlocalename"></a>CD2DTextLayout::SetLocaleName  
 Establece el nombre de la configuración regional para el texto dentro de un intervalo de texto especificado  
  
```  
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Parámetros  
 `pwzLocaleName`  
 Una cadena de nombre de configuración regional terminada en null  
  
 `textRange`  
 Intervalo de texto al que se aplica este cambio  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve TRUE. De lo contrario, devuelve FALSE  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

