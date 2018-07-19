---
title: CClientDC (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: add135c353366ed54a24c63fcce2101c49d24fe7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338586"
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
|[CClientDC::m_hWnd](#m_hwnd)|El HWND de la ventana para el que este `CClientDC` es válido.|  
  
## <a name="remarks"></a>Comentarios  
 Esto significa que el contexto de dispositivo asociado a un `CClientDC` objeto es el área de cliente de una ventana.  
  
 Para obtener más información sobre `CClientDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cclientdc"></a>  CClientDC::CClientDC  
 Construye un `CClientDC` objeto que tiene acceso al área de cliente de la [CWnd](../../mfc/reference/cwnd-class.md) apunta *conquistado*.  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *conquistado*  
 La ventana cuyo área de cliente que tendrá acceso el objeto de contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a la función Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871).  
  
 Una excepción (de tipo `CResourceException`) se produce si el Windows `GetDC` llamar se produce un error. Un contexto de dispositivo no puede estar disponible si Windows ya asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco contextos mostrar comunes disponibles en un momento dado en Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CClientDC::m_hWnd  
 El `HWND` de la `CWnd` puntero usado para construir el `CClientDC` objeto.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 *m_hWnd* es una variable protegida.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CClientDC::CClientDC](#cclientdc).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)
