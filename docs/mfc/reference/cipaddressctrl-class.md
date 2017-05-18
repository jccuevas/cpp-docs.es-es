---
title: Clase CIPAddressCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
dev_langs:
- C++
helpviewer_keywords:
- IP address control
- Internet address edit box
- CIPAddressCtrl class
- Internet protocol address box
- common controls, Internet Explorer 4.0
- Internet Explorer 4.0 common controls
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b3849580c7bfd07f241e55cc48144959566d7d09
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cipaddressctrl-class"></a>Clase CIPAddressCtrl
Proporciona la funcionalidad del control de dirección IP común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Construye un objeto `CIPAddressCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Borra el contenido del Control de dirección IP.|  
|[CIPAddressCtrl::Create](#create)|Crea un Control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.|  
|[CIPAddressCtrl::CreateEx](#createex)|Crea un control de dirección IP con los estilos extendidos de Windows especificados y lo adjunta a un `CIPAddressCtrl` objeto.|  
|[CIPAddressCtrl::GetAddress](#getaddress)|Recupera los valores de dirección para los cuatro campos en el Control de dirección IP.|  
|[CIPAddressCtrl::IsBlank](#isblank)|Determina si el Control de dirección IP de todos los campos están vacíos.|  
|[CIPAddressCtrl::SetAddress](#setaddress)|Establece los valores de dirección de los cuatro campos en el Control de dirección IP.|  
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Establece el foco del teclado en el campo especificado en el Control de dirección IP.|  
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Establece el intervalo en el campo especificado en el Control de dirección IP.|  
  
## <a name="remarks"></a>Comentarios  
 Un control de dirección IP, un control similar a un control de edición permite escribir y manipular una dirección numérica en formato de protocolo de Internet (IP).  
  
 Este control (y por tanto la `CIPAddressCtrl` clase) sólo está disponible para programas que se ejecutan en Microsoft Internet Explorer 4.0 y versiones posteriores. También estará disponibles en versiones futuras de Windows y Windows NT.  
  
 Para obtener información general sobre el Control de dirección IP, consulte [controles de dirección IP](http://msdn.microsoft.com/library/windows/desktop/bb761372) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl  
 Crea un objeto `CIPAddressCtrl`.  
  
```  
CIPAddressCtrl();
```  
  
##  <a name="clearaddress"></a>CIPAddressCtrl::ClearAddress  
 Borra el contenido del Control de dirección IP.  
  
```  
void ClearAddress();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_CLEARADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761377), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="create"></a>CIPAddressCtrl::Create  
 Crea un Control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el **WS_CHILD** porque el control debe ser una ventana secundaria de estilo. Consulte [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de estilos de windows.  
  
 `rect`  
 Referencia al tamaño y la posición del Control de dirección IP. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.  
  
 `pParentWnd`  
 Puntero a la ventana primaria del Control de dirección IP. No debe ser **NULL.**  
  
 `nID`  
 Identificador. del Control de dirección IP  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CIPAddressCtrl` objeto en dos pasos.  
  
1.  Llame al constructor, que crea el `CIPAddressCtrl` objeto.  
  
2.  Llame a **crear**, que crea el Control de dirección IP.  
  
 Si desea utilizar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de **crear**.  
  
##  <a name="createex"></a>CIPAddressCtrl::CreateEx  
 Llame a esta función para crear un control (una ventana secundaria) y asociarla con el `CIPAddressCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el **WS_CHILD** porque el control debe ser una ventana secundaria de estilo. Consulte [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de estilos de windows.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente `pParentWnd`.  
  
 `pParentWnd`  
 Puntero a la ventana que es principal el control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="getaddress"></a>CIPAddressCtrl::GetAddress  
 Recupera los valores de dirección para los cuatro campos en el Control de dirección IP.  
  
```  
int GetAddress(
    BYTE& nField0,  
    BYTE& nField1,  
    BYTE& nField2,  
    BYTE& nField3);  
  
int GetAddress(DWORD& dwAddress);
```  
  
### <a name="parameters"></a>Parámetros  
 `nField0`  
 Una referencia al valor del campo 0 desde una dirección IP empaquetada.  
  
 `nField1`  
 Una referencia al valor del campo 1 desde una dirección IP empaquetada.  
  
 `nField2`  
 Una referencia al valor del campo 2 desde una dirección IP empaquetada.  
  
 `nField3`  
 Una referencia al valor del campo 3 desde una dirección IP empaquetada.  
  
 `dwAddress`  
 Una referencia a la dirección de un `DWORD` valor que recibe la dirección IP. Consulte **comentarios** para una tabla que muestra cómo `dwAddress` se rellena.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos en blanco en el Control de dirección IP.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En el primer prototipo, los números en los campos de 0 a 3 del control, leer de izquierda a derecha respectivamente, rellenar los cuatro parámetros. En el segundo prototipo anterior, `dwAddress` se rellena como sigue.  
  
|Campo|Que contiene el valor del campo de bits|  
|-----------|-------------------------------------|  
|0|24 a 31|  
|1|16 a 23|  
|2|8 a 15|  
|3|de 0 a 7|  
  
##  <a name="isblank"></a>CIPAddressCtrl::IsBlank  
 Determina si el Control de dirección IP de todos los campos están vacíos.  
  
```  
BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si todos los campos del Control de dirección IP están vacías; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_ISBLANK](http://msdn.microsoft.com/library/windows/desktop/bb761379), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setaddress"></a>CIPAddressCtrl::SetAddress  
 Establece los valores de dirección de los cuatro campos en el Control de dirección IP.  
  
```  
void SetAddress(
    BYTE nField0,  
    BYTE nField1,  
    BYTE nField2,  
    BYTE nField3);  
  
void SetAddress(DWORD dwAddress);
```  
  
### <a name="parameters"></a>Parámetros  
 `nField0`  
 El valor del campo 0 desde una dirección IP empaquetado.  
  
 `nField1`  
 El valor del campo 1 desde una dirección IP empaquetado.  
  
 `nField2`  
 El valor del campo 2 desde una dirección IP empaquetado.  
  
 `nField3`  
 El valor del campo 3 desde una dirección IP empaquetado.  
  
 `dwAddress`  
 Un `DWORD` valor que contiene la nueva dirección IP. Consulte **comentarios** para una tabla que muestra cómo el `DWORD` valor se rellena.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En el primer prototipo, los números en los campos de 0 a 3 del control, leer de izquierda a derecha respectivamente, rellenar los cuatro parámetros. En el segundo prototipo anterior, `dwAddress` se rellena como sigue.  
  
|Campo|Que contiene el valor del campo de bits|  
|-----------|-------------------------------------|  
|0|24 a 31|  
|1|16 a 23|  
|2|8 a 15|  
|3|de 0 a 7|  
  
##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus  
 Establece el foco del teclado en el campo especificado en el Control de dirección IP.  
  
```  
void SetFieldFocus(WORD nField);
```  
  
### <a name="parameters"></a>Parámetros  
 `nField`  
 Índice del campo de base cero a la que se debe establecer el foco. Si este valor es mayor que el número de campos, el foco se establece en el primer campo en blanco. Si todos los campos en blanco, el foco se establece en el primer campo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb761381), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange  
 Establece el intervalo en el campo especificado en el Control de dirección IP.  
  
```  
void SetFieldRange(
    int nField,  
    BYTE nLower,  
    BYTE nUpper);
```  
  
### <a name="parameters"></a>Parámetros  
 `nField`  
 Índice del campo de base cero a la que se aplicará el intervalo.  
  
 `nLower`  
 Una referencia a un entero que recibir el límite inferior del campo especificado en este Control de dirección IP.  
  
 `nUpper`  
 Una referencia a un entero que recibir el límite superior del campo especificado en este Control de dirección IP.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761382), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Utilice los dos parámetros, `nLower` y `nUpper`, para indicar los límites superiores e inferiores del campo, en lugar de la *wRange* parámetro utilizado con el mensaje de Win32.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




