---
title: Clase CD2DTextFormat | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CD2DTextFormat
- CD2DTextFormat
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextFormat class
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5f7347dbbad8290bfdc800cbacaf21400583a392
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dtextformat-class"></a>Clase CD2DTextFormat
Un contenedor para IDWriteTextFormat.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Construye un objeto CD2DTextFormat.|  
|[CD2DTextFormat:: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|Destructor. Se llama cuando se destruye un objeto de formato de texto de D2D.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::Create](#create)|Crea un CD2DTextFormat. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextFormat::Destroy](#destroy)|Destruye un objeto CD2DTextFormat. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextFormat::Get](#get)|Interfaz de IDWriteTextFormat devuelve|  
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Obtiene una copia del nombre de familia de fuentes.|  
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Obtiene una copia del nombre de la configuración regional.|  
|[CD2DTextFormat::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextFormat::ReCreate](#recreate)|Vuelve a crear un CD2DTextFormat. (Invalida [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::operator IDWriteTextFormat *](#operator_idwritetextformat_star)|Interfaz de IDWriteTextFormat devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Puntero a un IDWriteTextFormat.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="a-namedtorcd2dtextformata--cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2DTextFormat:: ~ CD2DTextFormat  
 Destructor. Se llama cuando se destruye un objeto de formato de texto de D2D.  
  
```  
virtual ~CD2DTextFormat();
```  
  
##  <a name="a-namecd2dtextformata--cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2DTextFormat::CD2DTextFormat  
 Construye un objeto CD2DTextFormat.  
  
```  
CD2DTextFormat(
    CRenderTarget* pParentTarget,  
    const CString& strFontFamilyName,  
    FLOAT fontSize,  
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,  
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,  
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,  
    const CString& strFontLocale = _T(""),  
    IDWriteFontCollection* pFontCollection = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentTarget`  
 Puntero para el destino de representación.  
  
 `strFontFamilyName`  
 Un objeto CString que contiene el nombre de la familia de fuentes.  
  
 `fontSize`  
 El tamaño lógico de la fuente en unidades DIP ("píxeles independientes del dispositivo"). Un DIPequals 1/96 de pulgada.  
  
 `fontWeight`  
 Un valor que indica el espesor de fuente para el objeto de texto.  
  
 `fontStyle`  
 Un valor que indica el estilo de fuente para el objeto de texto.  
  
 `fontStretch`  
 Un valor que indica el estiramiento de fuente para el objeto de texto.  
  
 `strFontLocale`  
 Un objeto CString que contiene el nombre de la configuración regional.  
  
 `pFontCollection`  
 Puntero a un objeto de colección de la fuente. Cuando es NULL, indica la colección de fuentes del sistema.  
  
 `bAutoDestroy`  
 Indica que se destruirá el objeto propietario (pParentTarget).  
  
##  <a name="a-namecreatea--cd2dtextformatcreate"></a><a name="create"></a>CD2DTextFormat::Create  
 Crea un CD2DTextFormat.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="a-namedestroya--cd2dtextformatdestroy"></a><a name="destroy"></a>CD2DTextFormat::Destroy  
 Destruye un objeto CD2DTextFormat.  
  
```  
virtual void Destroy();
```  
  
##  <a name="a-namegeta--cd2dtextformatget"></a><a name="get"></a>CD2DTextFormat::Get  
 Interfaz de IDWriteTextFormat devuelve  
  
```  
IDWriteTextFormat* Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz IDWriteTextFormat o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="a-namegetfontfamilynamea--cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextFormat::GetFontFamilyName  
 Obtiene una copia del nombre de familia de fuentes.  
  
```  
CString GetFontFamilyName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto CString que contiene el nombre de familia de fuentes actual.  
  
##  <a name="a-namegetlocalenamea--cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2DTextFormat::GetLocaleName  
 Obtiene una copia del nombre de la configuración regional.  
  
```  
CString GetLocaleName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto CString que contiene el nombre de la configuración regional actual.  
  
##  <a name="a-nameisvalida--cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2DTextFormat::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válido; de lo contrario, FALSE.  
  
##  <a name="a-namemptextformata--cd2dtextformatmptextformat"></a><a name="m_ptextformat"></a>CD2DTextFormat::m_pTextFormat  
 Puntero a un IDWriteTextFormat.  
  
```  
IDWriteTextFormat* m_pTextFormat;  
```  
  
##  <a name="a-nameoperatoridwritetextformatstara--cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2DTextFormat::operator IDWriteTextFormat *  
 Interfaz de IDWriteTextFormat devuelve  
  
```  
operator IDWriteTextFormat*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz IDWriteTextFormat o NULL si el objeto no se ha inicializado todavía.  
  
##  <a name="a-namerecreatea--cd2dtextformatrecreate"></a><a name="recreate"></a>CD2DTextFormat::ReCreate  
 Vuelve a crear un CD2DTextFormat.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

