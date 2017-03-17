---
title: CPaintDC (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- OnPaint handler
- WM_PAINT message
- CPaintDC class
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
caps.latest.revision: 22
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
ms.openlocfilehash: b781db7d4a6676e6fc6ad5df7553b9c9a0154ab9
ms.lasthandoff: 02/24/2017

---
# <a name="cpaintdc-class"></a>CPaintDC (clase)
Deriva una clase de contexto de dispositivo [CDC](../../mfc/reference/cdc-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPaintDC : public CDC  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPaintDC::CPaintDC](#cpaintdc)|Construye un `CPaintDC` conectado a especificado [CWnd](../../mfc/reference/cwnd-class.md).|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPaintDC::m_ps](#m_ps)|Contiene el [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) utilizado para pintar el área de cliente.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPaintDC::m_hWnd](#m_hwnd)|El `HWND` a la que se `CPaintDC` se adjunta el objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Realiza una [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) en tiempo de construcción y [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) en tiempo de destrucción.  
  
 Un `CPaintDC` objeto solo puede usarse cuando responde a un [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) de mensajes, normalmente en su `OnPaint` función de miembro de controlador de mensajes.  
  
 Para obtener más información sobre el uso de `CPaintDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cpaintdc"></a>CPaintDC::CPaintDC  
 Construye un `CPaintDC` prepara la ventana de la aplicación para dibujar el objeto y almacena el [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) estructura en el [m_ps](#m_ps) variable miembro.  
  
```  
explicit CPaintDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la `CWnd` objeto al que la `CPaintDC` objeto pertenece.  
  
### <a name="remarks"></a>Comentarios  
 Una excepción (de tipo `CResourceException`) se produce si Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) llamada produce un error. Un contexto de dispositivo no esté disponible si Windows ya asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco comunes contextos de presentación disponibles en cualquier momento en Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#97;](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>CPaintDC::m_hWnd  
 El `HWND` a la que se `CPaintDC` se adjunta el objeto.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_hWnd`es una variable de tipo protegida `HWND`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#98;](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]  
  
##  <a name="m_ps"></a>CPaintDC::m_ps  
 `m_ps`es una variable de miembro público del tipo [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md).  
  
```  
PAINTSTRUCT m_ps;  
```  
  
### <a name="remarks"></a>Comentarios  
 Es el `PAINTSTRUCT` que se pasa a y rellenado por [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).  
  
 El `PAINTSTRUCT` contiene información que la aplicación se utiliza para pintar el área de cliente de la ventana asociada a un `CPaintDC` objeto.  
  
 Tenga en cuenta que puede tener acceso al identificador del contexto de dispositivo a través de la `PAINTSTRUCT`. Sin embargo, puede tener acceso el controlador más directamente a través de la `m_hDC` variable miembro que `CPaintDC` hereda de `CDC`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPaintDC::m_hWnd](#m_hwnd).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




