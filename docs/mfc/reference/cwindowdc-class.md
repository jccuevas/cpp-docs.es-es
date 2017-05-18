---
title: Clase de los objetos CWindowDC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWindowDC
- No header/CWindowDC
- No header/CWindowDC::CWindowDC
- No header/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- device contexts, window
- screen output classes
- CWindowDC class
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
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
ms.openlocfilehash: 8a941e1b6f8a398706498ec5d1ce1bfc9156f115
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cwindowdc-class"></a>Clase de los objetos CWindowDC
Se deriva de `CDC`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|Construye un objeto `CWindowDC`.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|El `HWND` a la que se `CWindowDC` se adjunta.|  
  
## <a name="remarks"></a>Comentarios  
 Llama a la función de Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)en tiempo de construcción y [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx) en tiempo de destrucción. Esto significa que un `CWindowDC` objeto tiene acceso el área de pantalla completa de un [CWnd](../../mfc/reference/cwnd-class.md) (áreas cliente y no cliente).  
  
 Para obtener más información sobre el uso de `CWindowDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: afxwin.h  
  
##  <a name="cwindowdc"></a>CWindowDC::CWindowDC  
 Construye un `CWindowDC` objeto que tiene acceso el área de pantalla completa (cliente y no cliente) de la `CWnd` objeto señalado por `pWnd`.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 La ventana cuyo área de cliente que tendrá acceso el objeto de contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a la función de Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947).  
  
 Una excepción (de tipo `CResourceException`) se produce si Windows `GetWindowDC` llamada produce un error. Un contexto de dispositivo no esté disponible si Windows ya asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco comunes contextos de presentación disponibles en cualquier momento en Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#188;](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>CWindowDC::m_hWnd  
 El `HWND` de la `CWnd` puntero se utiliza para construir el `CWindowDC` objeto.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_hWnd`es una variable de tipo protegida `HWND`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWindowDC::CWindowDC](#cwindowdc).  
  
## <a name="see-also"></a>Vea también  
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)

