---
title: Clase CMFCAcceleratorKey | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey class
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: 36
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
ms.openlocfilehash: 7baa210acfabe8f17e2ab747fd98fe463c2907a2
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcacceleratorkey-class"></a>Clase CMFCAcceleratorKey
Clase auxiliar que implementa la asignación de clave virtual y el formato.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Construye un objeto `CMFCAcceleratorKey`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|Convierte la estructura de aceleración en su representación visual.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Establece la tecla de método abreviado para el `CMFCAcceleratorKey` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Teclas de aceleración también conocido como son teclas de método abreviado. Si desea mostrar métodos abreviados de teclado que un usuario escribe, la [CMFCAcceleratorKeyAssignCtrl clase](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapas abreviados, por ejemplo, Alt + Mayús + S a un formato de texto personalizado, como "Alt + Mayús + S". Cada `CMFCAcceleratorKey` objeto asigna un único método abreviado a un formato de texto.  
  
 Para obtener más información sobre cómo usar las teclas de método abreviado y tablas de aceleradores, consulte [CKeyboardManager clase](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCAcceleratorKey` objeto y cómo usar su `Format` método.  
  
 [!code-cpp[NVC_MFC_RibbonApp Nº&30;](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxacceleratorkey.h  
  
##  <a name="a-namecmfcacceleratorkeya--cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey  
 Construye un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpAccel`  
 Puntero a una tecla de método abreviado.  
  
### <a name="remarks"></a>Comentarios  
 Si no proporciona una tecla de método abreviado cuando se crea un `CMFCAccleratorKey`, utilice el [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) para asociar una tecla de método abreviado con su `CMFCAcceleratorKey` objeto.  
  
##  <a name="a-nameformata--cmfcacceleratorkeyformat"></a><a name="format"></a>CMFCAcceleratorKey::Format  
 Convierte la estructura de la tecla de aceleración a su valor de cadena asociado.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `str`  
 Una referencia a un `CString` donde el método escribe el método abreviado traducido del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera el formato de cadena de la tecla de método abreviado. Puede establecer el formato de cadena de un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto utilizando el constructor o el método [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="a-namesetacceleratora--cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator  
 Establece la tecla de método abreviado para el [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpAccel`  
 Puntero a una tecla de método abreviado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer la tecla de método abreviado para un `CMFCAcceleratorKey` si no se ha proporcionado una tecla de método abreviado cuando creó el `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

