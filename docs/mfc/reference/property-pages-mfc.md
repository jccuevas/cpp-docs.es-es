---
title: Páginas de propiedades (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 6456a192a502a0fcc032eaefc667c90ecec86d42
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751142"
---
# <a name="property-pages-mfc"></a>Páginas de propiedades (MFC)

Las páginas de propiedades muestran los valores actuales de propiedades de control OLE específicas en una interfaz gráfica personalizable para ver y editar mediante la compatibilidad con un mecanismo de asignación de datos basado en el intercambio de datos de cuadro de diálogo (DDX).

Este mecanismo de asignación de datos asigna controles de página de propiedades a las propiedades individuales del control OLE. El valor de la propiedad de control refleja el estado o el contenido del control de página de propiedades. La asignación entre los controles de **DDP_** página de propiedades y `DoDataExchange` las propiedades se especifica mediante DDP_ llamadas a funciones en la función miembro de la página de propiedades. A continuación se muestra una lista de **DDP_** funciones que intercambian datos introducidos mediante la página de propiedades del control:

### <a name="property-page-data-transfer"></a>Transferencia de datos de página de propiedades

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Vincula el índice de la cadena seleccionada en un cuadro combinado con la propiedad de un control.|
|[DDP_CBString](#ddp_cbstring)|Vincula la cadena seleccionada en un cuadro combinado con la propiedad de un control. La cadena seleccionada puede comenzar con las mismas letras que el valor de la propiedad, pero no es necesario que coincida completamente.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Vincula la cadena seleccionada en un cuadro combinado con la propiedad de un control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|[DDP_Check](#ddp_check)|Vincula una casilla de verificación en la página de propiedades del control con la propiedad de un control.|
|[DDP_LBIndex](#ddp_lbindex)|Vincula el índice de la cadena seleccionada en un cuadro de lista con la propiedad de un control.|
|[DDP_LBString](#ddp_lbstring)|Vincula la cadena seleccionada en un cuadro de lista con la propiedad de un control. La cadena seleccionada puede comenzar con las mismas letras que el valor de la propiedad, pero no es necesario que coincida completamente.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Vincula la cadena seleccionada en un cuadro de lista con la propiedad de un control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|[DDP_PostProcessing](#ddp_postprocessing)|Finaliza la transferencia de valores de propiedad desde el control.|
|[DDP_Radio](#ddp_radio)|Vincula un grupo de botones de opción en la página de propiedades del control con la propiedad de un control.|
|[DDP_Text](#ddp_text)|Vincula un control en la página de propiedades del control con la propiedad de un control. Esta función controla varios tipos diferentes de propiedades, como **double**, **short**, BSTR y **long**.|

Para obtener más `DoDataExchange` información acerca de las páginas de funciones y propiedades, vea el artículo [Controles ActiveX: Páginas](../../mfc/mfc-activex-controls-property-pages.md)de propiedades .

A continuación se muestra una lista de macros que se usan para crear y administrar páginas de propiedades para un control OLE:

### <a name="property-pages"></a>Páginas de propiedades

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Comienza la lista de ID de página de propiedades.|
|[END_PROPPAGEIDS](#end_proppageids)|Finaliza la lista de ID de página de propiedades.|
|[PROPPAGEID](#proppageid)|Declara una página de propiedades de la clase de control.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

Llame a esta función `DoDataExchange` en la función de la página de propiedades para sincronizar el valor de una propiedad entera con el índice de la selección actual en un cuadro combinado en la página de propiedades.

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de cuadro combinado asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con el control de cuadro combinado especificado por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_CBIndex`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

Llame a esta función `DoDataExchange` en la función de la página de propiedades para sincronizar el valor de una propiedad de cadena con la selección actual en un cuadro combinado en la página de propiedades.

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de cuadro combinado asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con la cadena de cuadro combinado especificada por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_CBString`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

Llame a esta función `DoDataExchange` en la función de la página de propiedades para sincronizar el valor de una propiedad de cadena que coincida exactamente con la selección actual en un cuadro combinado en la página de propiedades.

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de cuadro combinado asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con la cadena de cuadro combinado especificada por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_CBStringExact`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

Llame a esta función `DoDataExchange` en la función de la página de propiedades para sincronizar el valor de la propiedad con el control de casilla de verificación de página de propiedades asociado.

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de casilla de verificación asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con el control de casilla de verificación especificado por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_Check`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

Llame a esta función `DoDataExchange` en la función de la página de propiedades para sincronizar el valor de una propiedad entera con el índice de la selección actual en un cuadro de lista en la página de propiedades.

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de cuadro de lista asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con la cadena de cuadro de lista especificada por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_LBIndex`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

Llame a esta función `DoDataExchange` en la función de la página de propiedades para sincronizar el valor de una propiedad de cadena con la selección actual en un cuadro de lista en la página de propiedades.

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de cuadro de lista asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con la cadena de cuadro de lista especificada por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_LBString`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

Llame a esta función `DoDataExchange` en la función de la página de propiedades para sincronizar el valor de una propiedad de cadena que coincida exactamente con la selección actual en un cuadro de lista de la página de propiedades.

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de cuadro de lista asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con la cadena de cuadro de lista especificada por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_LBStringExact`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

Llame a esta función `DoDataExchange` en la función de la página de propiedades para finalizar la transferencia de valores de propiedad desde la página de propiedades al control cuando se guardan los valores de propiedad.

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse una vez completadas todas las funciones de intercambio de datos. Por ejemplo:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

Llame a esta función `DoPropExchange` en la función del control para sincronizar el valor de la propiedad con el control de botón de opción de página de propiedades asociado.

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control de botón de opción asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con el control de botón de opción especificado por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_Radio`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

Llame a esta función `DoDataExchange` en la función del control para sincronizar el valor de la propiedad con el control de página de propiedades asociado.

```cpp
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a `CDataExchange` un objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*id*<br/>
El identificador de recurso del control asociado a la propiedad de control especificada por *pszPropName*.

*Miembro*<br/>
La variable miembro asociada al control de página de propiedades especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que se va a intercambiar con el control especificado por *id*.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse antes de la llamada de función correspondiente. `DDX_Text`

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

Comienza la definición de la lista de id de página de propiedades del control.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control para la que se especifican las páginas de propiedades.

*count*<br/>
El número de páginas de propiedades utilizadas por la clase de control.

### <a name="remarks"></a>Observaciones

En el archivo de implementación (.cpp) que define las funciones miembro de la clase, inicie la lista de páginas de propiedades con la macro BEGIN_PROPPAGEIDS, agregue entradas de macro para cada una de las páginas de propiedades y complete la lista de páginas de propiedades con la macro END_PROPPAGEIDS.

Para obtener más información sobre las páginas de propiedades, vea el artículo [Controles ActiveX: Páginas](../../mfc/mfc-activex-controls-property-pages.md)de propiedades .

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

Finaliza la definición de la lista de IDENTIFICADORes de página de propiedades.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control que posee la página de propiedades.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>PROPPAGEID

Agrega una página de propiedades para su uso por el control OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
El identificador de clase único de una página de propiedades.

### <a name="remarks"></a>Observaciones

Todas las macros PROPPAGEID deben colocarse entre las macros BEGIN_PROPPAGEIDS y END_PROPPAGEIDS en el archivo de implementación del control.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="see-also"></a>Vea también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
