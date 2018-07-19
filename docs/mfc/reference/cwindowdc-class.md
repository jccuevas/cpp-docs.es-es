---
title: Clase de los objetos CWindowDC | Documentos de Microsoft
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
ms.openlocfilehash: 8b757da27f2b4ae79a0192df0598f833b3d1e7b9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121547"
---
# <a name="cwindowdc-class"></a>Clase de los objetos CWindowDC
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
|[CWindowDC::m_hWnd](#m_hwnd)|El HWND a la que se `CWindowDC` se adjunta.|  
  
## <a name="remarks"></a>Comentarios  
 Llama a la función de Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)en tiempo de construcción y [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx) en tiempo de destrucción. Esto significa que un `CWindowDC` objeto obtiene acceso al área de pantalla completa de un [CWnd](../../mfc/reference/cwnd-class.md) (las áreas de cliente y de cliente).  
  
 Para obtener más información sobre el uso de `CWindowDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Construye un `CWindowDC` objeto que tiene acceso el área de pantalla completa (cliente y no cliente) de la `CWnd` objeto señalado por *pWnd*.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWnd*  
 La ventana cuyo área de cliente tendrá acceso los objetos de contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a la función de Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947).  
  
 Una excepción (de tipo `CResourceException`) se produce si las ventanas `GetWindowDC` llamadas se produce un error. Un contexto de dispositivo no estén disponible si Windows ya ha asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco comunes contextos de presentación disponibles en un momento dado en Windows.  
  
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
