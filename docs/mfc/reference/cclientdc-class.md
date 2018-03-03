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
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a92fb471ee30e725cd97bff6cbda8d551c0bc859
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cclientdc-class"></a>CClientDC (clase)
Se encarga de llamar a las funciones de Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) en tiempo de construcción y [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) en tiempo de destrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CClientDC : public CDC  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CClientDC::CClientDC](#cclientdc)|Construye un `CClientDC` objeto conectado a la `CWnd`.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CClientDC::m_hWnd](#m_hwnd)|El `HWND` de la ventana para el que este `CClientDC` es válida.|  
  
## <a name="remarks"></a>Comentarios  
 Esto significa que el contexto de dispositivo asociado a un `CClientDC` objeto es el área de cliente de una ventana.  
  
 Para obtener más información sobre `CClientDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cclientdc"></a>CClientDC::CClientDC  
 Construye un `CClientDC` objeto que tiene acceso el área cliente de la [CWnd](../../mfc/reference/cwnd-class.md) señalada por `pWnd`.  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 La ventana cuyo área de cliente accederá el objeto de contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a la función de Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871).  
  
 Una excepción (de tipo `CResourceException`) se produce si las ventanas `GetDC` llamadas se produce un error. Un contexto de dispositivo no estén disponible si Windows ya ha asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco comunes contextos de presentación disponibles en un momento dado en Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
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
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)
