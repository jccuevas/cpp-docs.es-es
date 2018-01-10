---
title: Clase CMFCAcceleratorKey | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs: C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3303be9f37749436d140028cd5fa45cd4454c8c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey (clase)
Una clase auxiliar que implementa la asignación de claves virtual y el formato.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Construye un objeto `CMFCAcceleratorKey`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|Convierte la estructura de la aceleración en su representación visual.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Establece la tecla de método abreviado para el `CMFCAcceleratorKey` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Teclas de aceleración son también conocido como teclas de método abreviado. Si desea mostrar los métodos abreviados de teclado que un usuario escribe, la [clase CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapas abreviados, como Alt + Mayús + S, en un formato de texto personalizado, como "Alt + Mayús + S". Cada `CMFCAcceleratorKey` objeto asigna un único método abreviado a un formato de texto.  
  
 Para obtener más información sobre cómo usar las teclas de método abreviado y tablas de aceleradores, consulte [CKeyboardManager clase](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCAcceleratorKey` objeto y cómo usar su `Format` método.  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey  
 Construye un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpAccel`  
 Un puntero a una tecla de método abreviado.  
  
### <a name="remarks"></a>Comentarios  
 Si no proporciona una tecla de método abreviado cuando se crea un `CMFCAccleratorKey`, use la [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) método para asociar una tecla de método abreviado con su `CMFCAcceleratorKey` objeto.  
  
##  <a name="format"></a>CMFCAcceleratorKey::Format  
 Traduce la estructura de aceleración a su valor de cadena asociado.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `str`  
 Una referencia a un `CString` donde el método escribe el método abreviado traducido del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera el formato de cadena de la clave de acceso directo asociado. Puede establecer el formato de cadena de un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto utilizando el constructor o el método [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator  
 Establece la tecla de método abreviado para el [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpAccel`  
 Un puntero a una tecla de método abreviado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer la tecla de método abreviado para un `CMFCAcceleratorKey` si no se proporcionó una tecla de método abreviado cuando creaste la `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager (clase)](../../mfc/reference/ckeyboardmanager-class.md)
