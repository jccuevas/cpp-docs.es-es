---
title: CClientDC (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CClientDC class
- device contexts, client area
- client-area device context
- CDC class, device contexts for client areas
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 619bed4d31994bde8464ad710e9f050d6ba0696a
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cclientdc-class"></a>CClientDC (clase)
Se encarga de llamar a las funciones de Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) en tiempo de construcción y [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) en tiempo de destrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CClientDC : public CDC  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CClientDC::CClientDC](#cclientdc)|Construye un `CClientDC` objeto conectado a la `CWnd`.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CClientDC::m_hWnd](#m_hwnd)|El `HWND` de la ventana para el que este `CClientDC` es válida.|  
  
## <a name="remarks"></a>Comentarios  
 Esto significa que el contexto de dispositivo asociado con un `CClientDC` objeto es el área de cliente de una ventana.  
  
 Para obtener más información sobre `CClientDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cclientdc"></a>CClientDC::CClientDC  
 Construye un `CClientDC` objeto que tiene acceso al área cliente de la [CWnd](../../mfc/reference/cwnd-class.md) señala `pWnd`.  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 La ventana cuyo área de cliente que tendrá acceso el objeto de contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a la función de Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871).  
  
 Una excepción (de tipo `CResourceException`) se produce si Windows `GetDC` llamada produce un error. Un contexto de dispositivo no esté disponible si Windows ya asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco comunes contextos de presentación disponibles en cualquier momento en Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#42;](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>CClientDC::m_hWnd  
 El `HWND` de la `CWnd` puntero utilizado para construir el `CClientDC` objeto.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_hWnd`es una variable protegida.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CClientDC::CClientDC](#cclientdc).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)

