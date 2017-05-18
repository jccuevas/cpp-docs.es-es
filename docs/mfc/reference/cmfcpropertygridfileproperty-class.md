---
title: Clase CMFCPropertyGridFileProperty | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFileProperty class
- CMFCPropertyGridFileProperty::OnClickButton method
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
caps.latest.revision: 25
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 56e9d258f5d608b03497632bef84cf73611f2e9a
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertygridfileproperty-class"></a>Clase CMFCPropertyGridFileProperty
La `CMFCPropertyGridFileProperty` clase es compatible con un elemento de control de lista de propiedades que se abre un cuadro de diálogo de selección de archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Construye un objeto `CMFCPropertyGridFileProperty`.|  
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCPropertyGridFileProperty::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|`CMFCPropertyGridFileProperty::OnClickButton`|(Invalida [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty  
 Construye un objeto `CMFCPropertyGridFileProperty`.  
  
```  
CMFCPropertyGridFileProperty(
    const CString& strName,  
    BOOL bOpenFileDialog,  
    const CString& strFileName,  
    LPCTSTR lpszDefExt=NULL,  
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter=NULL,  
    LPCTSTR lpszDescr=NULL,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strName`  
 Nombre de la propiedad.  
  
 [in] `bOpenFileDialog`  
 `TRUE`Para abrir un **abrir archivo** cuadro de diálogo; `FALSE` para abrir un **Guardar archivo** cuadro de diálogo.  
  
 [in] `strFileName`  
 El nombre de archivo inicial.  
  
 [in] `lpszDefExt`  
 Una cadena con una o más extensiones de nombre de archivo. El valor predeterminado es `NULL`.  
  
 [in] `dwFlags`  
 Marcas de cuadro de diálogo El valor predeterminado es una combinación bit a bit (OR) de `OFN_HIDEREADONLY` y `OFN_OVERWRITEPROMPT`.  
  
 [in] `lpszFilter`  
 Una cadena de uno o más filtros de archivo. El valor predeterminado es `NULL`.  
  
 [in] `lpszDescr`  
 Una descripción del elemento de propiedad. El valor predeterminado es `NULL`.  
  
 [in] `dwData`  
 Datos específicos de la aplicación que están asociados al elemento de propiedad. Por ejemplo, un entero de 32 bits o un puntero a otros datos. El valor predeterminado es 0.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una lista completa de los indicadores disponibles, vea [estructura OPENFILENAME](https://msdn.microsoft.com/library/ms646839.aspx).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto mediante el constructor de la clase `CMFCPropertyGridFileProperty`. Este ejemplo forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#22;](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [Clase CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

