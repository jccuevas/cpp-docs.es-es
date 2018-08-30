---
title: CWindowDC (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40566ab94c9708d7b31f88de0f96b4fc33675534
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212526"
---
# <a name="cwindowdc-class"></a>CWindowDC (clase)
Se deriva de `CDC`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|Construye un objeto `CWindowDC`.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|El HWND para que este `CWindowDC` se adjunta.|  
  
## <a name="remarks"></a>Comentarios  
 Llama a la función Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)en tiempo de construcción y [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) en tiempo de destrucción. Esto significa que un `CWindowDC` objeto obtiene acceso a un área de pantalla completa de un [CWnd](../../mfc/reference/cwnd-class.md) (áreas cliente y no cliente).  
  
 Para obtener más información sobre el uso de `CWindowDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Construye un `CWindowDC` objeto que tiene acceso al área de pantalla completa (cliente y no cliente) de la `CWnd` objeto señalado por *conquistado*.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *conquistado*  
 La ventana cuyo área de cliente que tendrá acceso el objeto de contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a la función Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc).  
  
 Una excepción (de tipo `CResourceException`) se produce si el Windows `GetWindowDC` llamar se produce un error. Un contexto de dispositivo no puede estar disponible si Windows ya asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco contextos mostrar comunes disponibles en un momento dado en Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd  
 El HWND de la `CWnd` puntero se utiliza para construir el `CWindowDC` objeto.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_hWnd` es una variable de tipo HWND protegida.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWindowDC::CWindowDC](#cwindowdc).  
  
## <a name="see-also"></a>Vea también  
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)
