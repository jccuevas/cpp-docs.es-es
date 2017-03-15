---
title: Clase CMFCAcceleratorKeyAssignCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl class
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
caps.latest.revision: 33
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
ms.openlocfilehash: 23687cf4c13881293d10a5f816a2c825180df49c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Clase CMFCAcceleratorKeyAssignCtrl
El `CMFCAcceleratorKeyAssignCtrl` clase extiende la [CEdit Class](../../mfc/reference/cedit-class.md) para admitir botones de sistema adicionales como ALT, CONTROL y MAYÚS.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Construye un objeto `CMFCAcceleratorKeyAssignCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Recupera la estructura `ACCEL` para una tecla de método abreviado pulsada en el objeto `CMFCAcceleratorKeyAssignCtrl`.|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Determina si se ha definido una tecla de método abreviado.|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Restablece la tecla de método abreviado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase extiende la funcionalidad de la clase `CEdit` ofreciendo compatibilidad con teclas de método abreviado, también conocido como teclas de aceleración. El `CMFCAcceleratorKeyAssignCtrl` clase funciona como un [CEdit Class](../../mfc/reference/cedit-class.md) y también puede reconocer los botones de sistema.  
  
 Esta clase asigna combinaciones de teclas físicas de método abreviado a valores de cadena. Por ejemplo, suponga que la combinación de teclas ALT + B se asigna a la cadena "Alt + B". Cuando el usuario presione esta combinación de teclas en un objeto `CMFCAcceleratorKeyAssignCtrl`, se le mostrará "Alt + B". Para obtener más información acerca de la asignación de teclas de método abreviado y un formato de cadena, vea [CMFCAcceleratorKey clase](../../mfc/reference/cmfcacceleratorkey-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto `CMFCAcceleratorKeyAssignCtrl` y utilizar su método `ResetKey` para restablecer la tecla de método abreviado.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#31;](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxacceleratorkeyassignctrl.h  
  
##  <a name="a-namecmfcacceleratorkeyassignctrla--cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 Construye un [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="a-namegetaccela--cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel  
 Recupera el `ACCEL` estructura para presiona una tecla de método abreviado en el [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `ACCEL` estructura que describe el método abreviado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para recuperar el `ACCEL` estructura de una tecla de método abreviado que el usuario ha escrito en su `CMFCAcceleratorKeyAssignCtrl` objeto.  
  
##  <a name="a-nameisfocuseda--cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameiskeydefineda--cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 Determina si se ha definido una tecla de método abreviado en el [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el usuario ya ha presionado una combinación válida de claves que definen una tecla de método abreviado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para determinar si el usuario ha escrito una clave de acceso directo válido en su `CMFCAcceleratorKeyAssignCtrl` objeto. Si existe un método abreviado, puede usar [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) método para obtener el `ACCEL` estructura asociada con esta tecla de método abreviado.  
  
##  <a name="a-namepretranslatemessagea--cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameresetkeya--cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey  
 Restablece la tecla de método abreviado.  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>Comentarios  
 La función borra el texto del control de edición. Esto incluye las teclas de método abreviado que el usuario presionó.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)

