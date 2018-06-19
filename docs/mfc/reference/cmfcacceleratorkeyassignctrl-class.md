---
title: Clase CMFCAcceleratorKeyAssignCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a2906071ce1e8c8f65f21554915feed0d134276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367950"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Clase CMFCAcceleratorKeyAssignCtrl
El `CMFCAcceleratorKeyAssignCtrl` clase extiende la [clase CEdit](../../mfc/reference/cedit-class.md) para ofrecer compatibilidad con teclas adicionales del sistema, como ALT, CONTROL y mayúsculas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Construye un objeto `CMFCAcceleratorKeyAssignCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Recupera la estructura `ACCEL` para una tecla de método abreviado pulsada en el objeto `CMFCAcceleratorKeyAssignCtrl`.|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Determina si se ha definido una tecla de método abreviado.|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|La clase [CWinApp](../../mfc/reference/cwinapp-class.md) lo usa para traducir los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) . (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Restablece la tecla de método abreviado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase extiende la funcionalidad de la clase `CEdit` ofreciendo compatibilidad con teclas de método abreviado, también conocido como teclas de aceleración. El `CMFCAcceleratorKeyAssignCtrl` clase funciona como un [clase CEdit](../../mfc/reference/cedit-class.md) y también lo puede reconocer teclas del sistema.  
  
 Esta clase asigna combinaciones de teclas físicas de método abreviado a valores de cadena. Por ejemplo, suponga que la combinación de teclas ALT + B se asigna a la cadena "Alt + B". Cuando el usuario presione esta combinación de teclas en un objeto `CMFCAcceleratorKeyAssignCtrl`, se le mostrará "Alt + B". Para obtener más información sobre las asignaciones entre las teclas de método abreviado y un formato de cadena, vea [CMFCAcceleratorKey (clase)](../../mfc/reference/cmfcacceleratorkey-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto `CMFCAcceleratorKeyAssignCtrl` y utilizar su método `ResetKey` para restablecer la tecla de método abreviado.  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxacceleratorkeyassignctrl.h  
  
##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 Construye un [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel  
 Recupera el `ACCEL` estructura para presiona una tecla de método abreviado en el [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `ACCEL` estructura que describe la tecla de método abreviado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para recuperar el `ACCEL` estructura de una tecla de método abreviado que el usuario ha escrito en su `CMFCAcceleratorKeyAssignCtrl` objeto.  
  
##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 Determina si se ha definido una tecla de método abreviado en el [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario ya ha presionado una combinación válida de claves que definen una tecla de método abreviado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para determinar si el usuario ha escrito una clave de acceso directo válido en su `CMFCAcceleratorKeyAssignCtrl` objeto. Si existe una tecla de método abreviado, puede usar [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) método para obtener el `ACCEL` estructura asociada con esta tecla de método abreviado.  
  
##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey  
 Restablece la tecla de método abreviado.  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>Comentarios  
 La función borra el texto del control de edición. Esto incluye las teclas de método abreviado que el usuario presionó.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey (clase)](../../mfc/reference/cmfcacceleratorkey-class.md)
