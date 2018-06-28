---
title: Clase CIPAddressCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3e5f88dc011e358c0438209f0a4b3e277419be9
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042162"
---
# <a name="cipaddressctrl-class"></a>Clase CIPAddressCtrl
Proporciona la funcionalidad del control de dirección IP común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Construye un objeto `CIPAddressCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Borra el contenido del Control de dirección IP.|  
|[CIPAddressCtrl::Create](#create)|Crea un Control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.|  
|[CIPAddressCtrl::CreateEx](#createex)|Crea un control de dirección IP con los estilos extendidos de Windows especificados y lo adjunta a un `CIPAddressCtrl` objeto.|  
|[CIPAddressCtrl::GetAddress](#getaddress)|Recupera los valores de dirección para los cuatro campos en el Control de dirección IP.|  
|[CIPAddressCtrl::IsBlank](#isblank)|Determina si todos los campos en el Control de dirección IP están vacíos.|  
|[CIPAddressCtrl::SetAddress](#setaddress)|Establece los valores de dirección para los cuatro campos en el Control de dirección IP.|  
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Establece el foco del teclado en el campo especificado en el Control de dirección IP.|  
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Establece la duración en el campo especificado en el Control de dirección IP.|  
  
## <a name="remarks"></a>Comentarios  
 Un control de dirección IP, un control similar a un control de edición, puede escribir y manipular una dirección numérica en formato de protocolo de Internet (IP).  
  
 Este control (y, por tanto, la `CIPAddressCtrl` clase) solo está disponible para programas que se ejecutan en Microsoft Internet Explorer 4.0 y versiones posteriores. También estará disponibles en versiones futuras de Windows y Windows NT.  
  
 Para obtener más información sobre el Control de dirección IP, consulte [controles de dirección IP](http://msdn.microsoft.com/library/windows/desktop/bb761372) en el SDK de Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="cipaddressctrl"></a>  CIPAddressCtrl::CIPAddressCtrl  
 Crea un objeto `CIPAddressCtrl`.  
  
```  
CIPAddressCtrl();
```  
  
##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress  
 Borra el contenido del Control de dirección IP.  
  
```  
void ClearAddress();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_CLEARADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761377), tal y como se describe en el SDK de Windows.  
  
##  <a name="create"></a>  CIPAddressCtrl::Create  
 Crea un Control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwStyle*  
 Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el **WS_CHILD** estilo porque el control debe ser una ventana secundaria. Vea [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) en el SDK de Windows para obtener una lista de estilos de windows.  
  
 *Rect*  
 Una referencia al tamaño y la posición del Control de dirección IP. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.  
  
 *pParentWnd*  
 Un puntero a la ventana primaria del Control de dirección IP. No debe ser **NULL.**  
  
 *nID*  
 Identificador. del Control de dirección IP  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CIPAddressCtrl` objeto en dos pasos.  
  
1.  Llame al constructor, que crea el `CIPAddressCtrl` objeto.  
  
2.  Llame a `Create`, que crea el Control de dirección IP.  
  
 Si desea utilizar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de `Create`.  
  
##  <a name="createex"></a>  CIPAddressCtrl::CreateEx  
 Llame a esta función para crear un control (una ventana secundaria) y asociarlo con el `CIPAddressCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwExStyle*  
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) del SDK de Windows.  
  
 *dwStyle*  
 Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el **WS_CHILD** estilo porque el control debe ser una ventana secundaria. Vea [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) en el SDK de Windows para obtener una lista de estilos de windows.  
  
 *Rect*  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.  
  
 *pParentWnd*  
 Un puntero a la ventana que es primario del control.  
  
 *nID*  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress  
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
 *nField0*  
 Una referencia al valor del campo 0 desde una dirección IP empaquetada.  
  
 *nField1*  
 Una referencia al valor del campo 1 desde una dirección IP empaquetada.  
  
 *nField2*  
 Una referencia al valor del campo 2 desde una dirección IP empaquetada.  
  
 *nField3*  
 Una referencia al valor del campo 3 desde una dirección IP empaquetada.  
  
 *dwAddress*  
 Una referencia a la dirección de un `DWORD` valor que recibe la dirección IP. Vea **comentarios** para una tabla que muestra cómo *dwAddress* se rellena.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos no están en blanco en el Control de dirección IP.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378), tal y como se describe en el SDK de Windows. En el primer prototipo, los números de 0 a 3 del control, campos de lectura de izquierda a derecha respectivamente, rellenar los cuatro parámetros. En el prototipo segundo anterior, *dwAddress* se rellena como sigue.  
  
|Campo|Que contiene el valor del campo de bits|  
|-----------|-------------------------------------|  
|0|24 a 31|  
|1|16 a 23|  
|2|8 a 15|  
|3|de 0 a 7|  
  
##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank  
 Determina si todos los campos en el Control de dirección IP están vacíos.  
  
```  
BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si todos los campos de Control de dirección IP están vacías; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_ISBLANK](http://msdn.microsoft.com/library/windows/desktop/bb761379), tal y como se describe en el SDK de Windows.  
  
##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress  
 Establece los valores de dirección para los cuatro campos en el Control de dirección IP.  
  
```  
void SetAddress(
    BYTE nField0,  
    BYTE nField1,  
    BYTE nField2,  
    BYTE nField3);  
  
void SetAddress(DWORD dwAddress);
```  
  
### <a name="parameters"></a>Parámetros  
 *nField0*  
 El valor del campo 0 desde una dirección IP empaquetado.  
  
 *nField1*  
 El valor del campo 1 desde una dirección IP empaquetado.  
  
 *nField2*  
 El valor del campo 2 desde una dirección IP empaquetado.  
  
 *nField3*  
 El valor del campo 3 desde una dirección IP empaquetado.  
  
 *dwAddress*  
 Un `DWORD` valor que contiene la nueva dirección IP. Vea **comentarios** para una tabla que muestra cómo el `DWORD` valor se rellena.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380), tal y como se describe en el SDK de Windows. En el primer prototipo, los números de 0 a 3 del control, campos de lectura de izquierda a derecha respectivamente, rellenar los cuatro parámetros. En el prototipo segundo anterior, *dwAddress* se rellena como sigue.  
  
|Campo|Que contiene el valor del campo de bits|  
|-----------|-------------------------------------|  
|0|24 a 31|  
|1|16 a 23|  
|2|8 a 15|  
|3|de 0 a 7|  
  
##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus  
 Establece el foco del teclado en el campo especificado en el Control de dirección IP.  
  
```  
void SetFieldFocus(WORD nField);
```  
  
### <a name="parameters"></a>Parámetros  
 *nCampo*  
 Índice del campo de base cero en el que se debe establecer el foco. Si este valor es mayor que el número de campos, el foco se establece en el primer campo en blanco. Si todos los campos están en blanco, el foco se establece en el primer campo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb761381), tal y como se describe en el SDK de Windows.  
  
##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange  
 Establece la duración en el campo especificado en el Control de dirección IP.  
  
```  
void SetFieldRange(
    int nField,  
    BYTE nLower,  
    BYTE nUpper);
```  
  
### <a name="parameters"></a>Parámetros  
 *nCampo*  
 Índice del campo de base cero a la que se aplicará el intervalo.  
  
 *nLower*  
 Una referencia a un entero que recibir el límite inferior del campo especificado en este Control de dirección IP.  
  
 *nUpper*  
 Una referencia a un entero que recibir el límite superior del campo especificado en este Control de dirección IP.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761382), tal y como se describe en el SDK de Windows. Use los dos parámetros, *nLower* y *nUpper*, para indicar los límites inferiores y superiores del campo, en lugar de la *wRange* parámetro utilizado con el mensaje de Win32.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



