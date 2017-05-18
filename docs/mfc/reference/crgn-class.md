---
title: CRgn (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
dev_langs:
- C++
helpviewer_keywords:
- HRGN
- CRgn class
- regions, MFC
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
caps.latest.revision: 23
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 3aa69aa3947409b5b3d96a9da92f5d4549eebbb4
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="crgn-class"></a>CRgn (clase)
Encapsula una región de la Interfaz de dispositivo gráfico (GDI) de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRgn : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRgn::CRgn](#crgn)|Construye un objeto `CRgn`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRgn::CombineRgn](#combinergn)|Establece un `CRgn` objeto para que sea equivalente a la unión de dos especificado `CRgn` objetos.|  
|[CRgn::CopyRgn](#copyrgn)|Establece un `CRgn` objeto para que sea una copia de un determinado `CRgn` objeto.|  
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicializa un `CRgn` objeto con una región elíptica.|  
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializa un `CRgn` objeto con una región elíptica definida por un [RECT](../../mfc/reference/rect-structure1.md) estructura.|  
|[CRgn::CreateFromData](#createfromdata)|Crea una región de los datos de transformación y región determinados.|  
|[CRgn::CreateFromPath](#createfrompath)|Crea una región de la ruta de acceso que se ha seleccionado en el contexto de dispositivo especificado.|  
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicializa un `CRgn` objeto con una región poligonal. El sistema cierra el polígono automáticamente, si es necesario, dibujando una línea desde el último vértice hasta la primera.|  
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicializa un `CRgn` objeto con una región que consta de una serie de polígonos cerrados. Los polígonos pueden ser separados, o pueden superponer.|  
|[CRgn::CreateRectRgn](#createrectrgn)|Inicializa un `CRgn` objeto con un área rectangular.|  
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializa un `CRgn` objeto con una región rectangular que define un [RECT](../../mfc/reference/rect-structure1.md) estructura.|  
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicializa un `CRgn` objeto con un área rectangular con esquinas redondeadas.|  
|[CRgn::EqualRgn](#equalrgn)|Comprueba dos `CRgn` objetos para determinar si son equivalentes.|  
|[CRgn::FromHandle](#fromhandle)|Devuelve un puntero a un `CRgn` objeto cuando se especifica un identificador a una región de Windows.|  
|[CRgn::GetRegionData](#getregiondata)|Llena el búfer especificado con los datos que describen la región especificada.|  
|[CRgn::GetRgnBox](#getrgnbox)|Recupera las coordenadas del rectángulo delimitador de un `CRgn` objeto.|  
|[CRgn::OffsetRgn](#offsetrgn)|Mueve un `CRgn` objeto por los desplazamientos indicados.|  
|[CRgn::PtInRegion](#ptinregion)|Determina si un punto especificado está en la región.|  
|[CRgn::RectInRegion](#rectinregion)|Determina si cualquier parte de un rectángulo especificado está dentro de los límites de la región.|  
|[CRgn::SetRectRgn](#setrectrgn)|Establece la `CRgn` objeto en la región rectangular especificada.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRgn::operator HRGN](#operator_hrgn)|Devuelve el identificador de Windows incluido en la `CRgn` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Una región es un área elíptico o poligonal dentro de una ventana. Para usar las regiones, utilice las funciones miembro de clase `CRgn` con las funciones de recorte definidas como miembros de clase `CDC`.  
  
 Las funciones miembro de `CRgn` crear, modificar y recuperar información sobre el objeto de región para la que se llama.  
  
 Para obtener más información sobre el uso de `CRgn`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="combinergn"></a>CRgn::CombineRgn  
 Crea una nueva área GDI combinando dos regiones existentes.  
  
```  
int CombineRgn(
    CRgn* pRgn1,  
    CRgn* pRgn2,  
    int nCombineMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn1`  
 Identifica un área existente.  
  
 `pRgn2`  
 Identifica un área existente.  
  
 `nCombineMode`  
 Especifica la operación que se realizará cuando la combinación de las regiones de origen de dos. Puede ser cualquiera de los siguientes valores:  
  
- **RGN_AND** usa las áreas superpuestas de ambas regiones (intersección).  
  
- **RGN_COPY** crea una copia de la región 1 (identificada por `pRgn1`).  
  
- **RGN_DIFF** crea una región que consta de las áreas de región 1 (identificada por `pRgn1`) que no forman parte de la región 2 (identificados por `pRgn2`).  
  
- **RGN_OR** combina ambas regiones en su totalidad (unión).  
  
- **RGN_XOR** combina ambas regiones pero quita las áreas superpuestas.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:  
  
- **COMPLEXREGION** nueva región tiene superpuesto en los bordes.  
  
- **ERROR** ninguna nueva área que creó.  
  
- **NULLREGION** nueva región está vacía.  
  
- **SIMPLEREGION** nueva región no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 Las regiones se combinan según lo especificado por `nCombineMode`.  
  
 Los dos especificados se combinan las regiones y el identificador de región resultante se almacena en la `CRgn` objeto. Por lo tanto, cualquier región se almacena en la `CRgn` objeto se reemplaza por la región combinada.  
  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Use [CopyRgn](#copyrgn) copiar simplemente una región en otra región.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]  
  
##  <a name="copyrgn"></a>CRgn::CopyRgn  
 Copia la región definida por `pRgnSrc` en la `CRgn` objeto.  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgnSrc`  
 Identifica un área existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:  
  
- **COMPLEXREGION** nueva región tiene superpuesto en los bordes.  
  
- **ERROR** ninguna nueva área que creó.  
  
- **NULLREGION** nueva región está vacía.  
  
- **SIMPLEREGION** nueva región no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 La nueva región reemplaza la región anteriormente almacenada en la `CRgn` objeto. Esta función es un caso especial de la [CombineRgn](#combinergn) función miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="createellipticrgn"></a>CRgn::CreateEllipticRgn  
 Crea una región elíptica.  
  
```  
BOOL CreateEllipticRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.  
  
 `y1`  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.  
  
 `x2`  
 Especifica la coordenada x lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.  
  
 `y2`  
 Especifica la coordenada y lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La región se define por el rectángulo delimitador especificado por `x1`, `y1`, `x2`, y `y2`. La región se almacena en la `CRgn` objeto.  
  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Cuando ha terminado de usar un área que se creó con la `CreateEllipticRgn` función, una aplicación debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitar el equipo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]  
  
##  <a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect  
 Crea una región elíptica.  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `RECT` estructura o un `CRect` objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha del rectángulo delimitador de la elipse.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La región se define mediante la estructura o el objeto al que señala `lpRect` y se almacena en la `CRgn` objeto.  
  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Cuando ha terminado de usar un área que se creó con la `CreateEllipticRgnIndirect` función, una aplicación debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitar el equipo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).  
  
##  <a name="createfromdata"></a>CRgn::CreateFromData  
 Crea una región de los datos de transformación y región determinados.  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpXForm*  
 Apunta a un [XFORM](../../mfc/reference/xform-structure.md) estructura de datos que define la transformación que se realizarán en la región. Si este puntero es **NULL**, se usa la transformación de identidad.  
  
 `nCount`  
 Especifica el número de bytes que señala `pRgnData`.  
  
 `pRgnData`  
 Apunta a un [RGNDATA](../../mfc/reference/rgndata-structure.md) estructura de datos que contiene los datos de la región.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación puede recuperar datos de una región mediante una llamada a la `CRgn::GetRegionData` (función).  
  
##  <a name="createfrompath"></a>CRgn::CreateFromPath  
 Crea una región de la ruta de acceso que se ha seleccionado en el contexto de dispositivo especificado.  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Identifica un contexto de dispositivo que contiene una ruta de acceso cerrada.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de dispositivo identificado por el `pDC` parámetro debe contener una ruta de acceso cerrada. Después de `CreateFromPath` convierte una ruta de acceso en una región, Windows descarta la ruta cerrada desde el contexto de dispositivo.  
  
##  <a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn  
 Crea una región poligonal.  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de **punto** estructuras o una matriz de `CPoint` objetos. Cada estructura especifica la coordenada x y Coordenada y de un vértice del polígono. El **punto** estructura tiene el formato siguiente:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `nCount`  
 Especifica el número de **punto** estructuras o `CPoint` objetos de la matriz señalada por `lpPoints`.  
  
 `nMode`  
 Especifica el modo de relleno para la región. Este parámetro puede ser **alternativo** o **generación**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El sistema cierra el polígono automáticamente, si es necesario, dibujando una línea desde el último vértice hasta la primera. La región resultante se almacena en la `CRgn` objeto.  
  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Cuando el modo de relleno de polígono es **alternativo**, el sistema rellena el área entre los lados de un polígono impares y pares en cada línea de barrido. Es decir, el sistema rellena el área entre el lado de la primero y la segundo, entre el lado tercero y cuarto y así sucesivamente.  
  
 Cuando el modo de relleno de polígono es **generación**, el sistema usa la dirección en la que se dibuja una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en un hacia la derecha o en una dirección hacia la izquierda. Cada vez que una línea imaginaria extraída de un área delimitada al exterior de una figura pasa a través de un segmento de línea a la derecha, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea a la izquierda, el recuento es reducido. El área se rellena si el recuento es distinto de cero cuando llega a la línea de la parte exterior de la ilustración.  
  
 Cuando una aplicación ha terminado de usar un área que se creó con la `CreatePolygonRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitar el equipo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]  
  
##  <a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn  
 Crea una región que consta de una serie de polígonos cerrados.  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de **punto** estructuras o una matriz de `CPoint` objetos que define los vértices de los polígonos. Cada polígono se debe cerrar explícitamente porque el sistema no cierre automáticamente. Los polígonos se especifican de forma consecutiva. El **punto** estructura tiene el formato siguiente:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `lpPolyCounts`  
 Apunta a una matriz de enteros. El primer entero especifica el número de vértices en el primer polígono en el `lpPoints` matriz, el segundo entero especifica el número de vértices en el polígono segundo y así sucesivamente.  
  
 `nCount`  
 Especifica el número total de enteros en la `lpPolyCounts` matriz.  
  
 `nPolyFillMode`  
 Especifica el modo de relleno de polígono. Este valor puede ser **alternativo** o **generación**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La región resultante se almacena en la `CRgn` objeto.  
  
 Los polígonos pueden ser separados, o pueden superponer.  
  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Cuando el modo de relleno de polígono es **alternativo**, el sistema rellena el área entre los lados de un polígono impares y pares en cada línea de barrido. Es decir, el sistema rellena el área entre el lado de la primero y la segundo, entre el lado tercero y cuarto y así sucesivamente.  
  
 Cuando el modo de relleno de polígono es **generación**, el sistema usa la dirección en la que se dibuja una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en un hacia la derecha o en una dirección hacia la izquierda. Cada vez que una línea imaginaria extraída de un área delimitada al exterior de una figura pasa a través de un segmento de línea a la derecha, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea a la izquierda, el recuento es reducido. El área se rellena si el recuento es distinto de cero cuando llega a la línea de la parte exterior de la ilustración.  
  
 Cuando una aplicación ha terminado de usar un área que se creó con la `CreatePolyPolygonRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función de miembro para quitarlo.  
  
##  <a name="createrectrgn"></a>CRgn::CreateRectRgn  
 Crea una región rectangular que se almacena en la `CRgn` objeto.  
  
```  
BOOL CreateRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x lógica de la esquina superior izquierda de la región.  
  
 `y1`  
 Especifica la coordenada y lógica de la esquina superior izquierda de la región.  
  
 `x2`  
 Especifica la coordenada x lógica de la esquina inferior derecha de la región.  
  
 `y2`  
 Especifica la coordenada y lógica de la esquina inferior derecha de la región.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Cuando ha terminado de usar una región creada por `CreateRectRgn`, una aplicación debe utilizar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función de miembro para quitar la región.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]  
  
 Para obtener un ejemplo adicional, consulte [CRgn::CombineRgn](#combinergn).  
  
##  <a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect  
 Crea una región rectangular que se almacena en la `CRgn` objeto.  
  
```  
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `RECT` estructura o `CRect` objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha de la región. El `RECT` estructura tiene el formato siguiente:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Cuando ha terminado de usar una región creada por `CreateRectRgnIndirect`, una aplicación debe utilizar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función de miembro para quitar la región.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]  
  
##  <a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn  
 Crea una región rectangular con esquinas redondeadas que se almacena en la `CRgn` objeto.  
  
```  
BOOL CreateRoundRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x lógica de la esquina superior izquierda de la región.  
  
 `y1`  
 Especifica la coordenada y lógica de la esquina superior izquierda de la región.  
  
 `x2`  
 Especifica la coordenada x lógica de la esquina inferior derecha de la región.  
  
 `y2`  
 Especifica la coordenada y lógica de la esquina inferior derecha de la región.  
  
 *x3*  
 Especifica el ancho de la elipse que se utiliza para crear las esquinas redondeadas.  
  
 `y3`  
 Especifica el alto de la elipse que se utiliza para crear las esquinas redondeadas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de una región se limita a 64 KB de memoria o las unidades lógicas de 32.767 por 32.767, lo que sea menor.  
  
 Cuando una aplicación ha terminado de usar un área que se creó con la `CreateRoundRectRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función de miembro para quitarlo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]  
  
##  <a name="crgn"></a>CRgn::CRgn  
 Construye un objeto `CRgn`.  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_hObject` miembro de datos no contiene una región de GDI de Windows válida hasta que se inicializa el objeto con uno o varios de los demás `CRgn` funciones miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateRoundRectRgn](#createroundrectrgn).  
  
##  <a name="equalrgn"></a>CRgn::EqualRgn  
 Determina si la región especificada es equivalente a la región que se almacenan en la `CRgn` objeto.  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Identifica un área.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si las dos regiones son equivalentes; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]  
  
##  <a name="fromhandle"></a>CRgn::FromHandle  
 Devuelve un puntero a un `CRgn` objeto cuando se especifica un identificador a una región de Windows.  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>Parámetros  
 `hRgn`  
 Especifica un identificador de una región de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CRgn` objeto. Si la función no se realizó correctamente, el valor devuelto es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CRgn` objeto ya no está asociado al identificador, un archivo temporal `CRgn` se crea y asocia el objeto. Este temporal `CRgn` objeto es válido solo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal todos los objetos se eliminan. Otra manera de decir esto es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
##  <a name="getregiondata"></a>CRgn::GetRegionData  
 Llena el búfer especificado con los datos que describen la región.  
  
```  
int GetRegionData(
    LPRGNDATA lpRgnData,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRgnData`  
 Apunta a un [RGNDATA](../../mfc/reference/rgndata-structure.md) estructura de datos que recibe la información. Si este parámetro es **NULL**, el valor devuelto contiene el número de bytes necesarios para los datos de la región.  
  
 `nCount`  
 Especifica el tamaño, en bytes, de la `lpRgnData` búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente y `nCount` especifica un número suficiente de bytes, el valor devuelto es siempre `nCount`. Si se produce un error en la función, o si `nCount` especifica menor que el número adecuado de bytes, el valor devuelto es 0 (error).  
  
### <a name="remarks"></a>Comentarios  
 Estos datos incluyen las dimensiones de los rectángulos que componen la región. Esta función se utiliza junto con el `CRgn::CreateFromData` función.  
  
##  <a name="getrgnbox"></a>CRgn::GetRgnBox  
 Recupera las coordenadas del rectángulo delimitador de la `CRgn` objeto.  
  
```  
int GetRgnBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `RECT` estructura o `CRect` objeto que recibe las coordenadas del rectángulo delimitador. El `RECT` estructura tiene el formato siguiente:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el tipo de la región. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** región tiene superpuesto en los bordes.  
  
- **NULLREGION** región está vacía.  
  
- **ERROR** `CRgn` objeto no especifica una región válida.  
  
- **SIMPLEREGION** región no tiene bordes superpuestos.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreatePolygonRgn](#createpolygonrgn).  
  
##  <a name="offsetrgn"></a>CRgn::OffsetRgn  
 Mueve la región que se almacenan en la `CRgn` objeto por los desplazamientos indicados.  
  
```  
int OffsetRgn(
    int x,  
    int y);  
  
int OffsetRgn(POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica el número de unidades para mover a la izquierda o derecha.  
  
 *y*  
 Especifica el número de unidades para mover hacia arriba o hacia abajo.  
  
 `point`  
 La coordenada x de `point` especifica el número de unidades para mover a la izquierda o derecha. La coordenada y de `point` especifica el número de unidades que se desplazan hacia arriba o hacia abajo. El `point` parámetro puede ser un **punto** estructura o un `CPoint` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de la nueva región. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** región tiene superpuesto en los bordes.  
  
- **ERROR** identificador de región no es válido.  
  
- **NULLREGION** región está vacía.  
  
- **SIMPLEREGION** región no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 La función mueve a la región *x* unidades a lo largo del eje x y *y* unidades a lo largo del eje y.  
  
 Los valores de las coordenadas de una región deben ser menor o igual que 32.767 y mayor o igual a -32.768. El *x* y *y* parámetros se deben elegir con cuidado para evitar que las coordenadas de región no válido.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="operator_hrgn"></a>CRgn::operator HRGN  
 Utilice este operador para obtener el identificador de GDI de Windows asociado de la `CRgn` objeto.  
  
```  
operator HRGN() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto GDI de Windows representado por la `CRgn` objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Éste es un operador de conversión, que admite el uso directo de un **HRGN** objeto.  
  
 Para obtener más información sobre el uso de objetos gráficos, vea el artículo [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ptinregion"></a>CRgn::PtInRegion  
 Comprueba si el punto indicado por *x* y *y* está en la región que se almacenan en la `CRgn` objeto.  
  
```  
BOOL PtInRegion(
    int x,  
    int y) const;  
  
BOOL PtInRegion(POINT point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del punto va a probar.  
  
 *y*  
 Especifica la coordenada y lógica del punto va a comprobar.  
  
 `point`  
 Las coordenadas x e y de `point` especificar las coordenadas x e y del punto para probar el valor de. El `point` parámetro puede ser un **punto** estructura o un `CPoint` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el punto está en la región; en caso contrario es 0.  
  
##  <a name="rectinregion"></a>CRgn::RectInRegion  
 Determina si cualquier parte del rectángulo especificado por `lpRect` está dentro de los límites de la región que se almacenan en la `CRgn` objeto.  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `RECT` estructura o `CRect` objeto. El `RECT` estructura tiene el formato siguiente:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si cualquier parte del rectángulo especificado se encuentra dentro de los límites de la región; en caso contrario es 0.  
  
##  <a name="setrectrgn"></a>CRgn::SetRectRgn  
 Crea una región rectangular.  
  
```  
void SetRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
void SetRectRgn(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x de la esquina superior izquierda de la región rectangular.  
  
 `y1`  
 Especifica la coordenada y de la esquina superior izquierda de la región rectangular.  
  
 `x2`  
 Especifica la coordenada x de la esquina inferior derecha de la región rectangular.  
  
 `y2`  
 Especifica la coordenada y de la esquina inferior derecha de la región rectangular.  
  
 `lpRect`  
 Especifica la región rectangular. Puede ser un puntero a un `RECT` estructura o un `CRect` objeto.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de [CreateRectRgn](#createrectrgn), sin embargo, no asigna memoria adicional del montón de aplicación de Windows local. En su lugar, usa el espacio asignado a la región que se almacena en la `CRgn` objeto. Esto significa que la `CRgn` objeto ya debe haber se ha inicializado con una región de Windows válida antes de llamar a `SetRectRgn`. Los puntos de proporcionado por `x1`, `y1`, `x2`, y `y2` especificar el tamaño mínimo de espacio asignado.  
  
 Use esta función en lugar de la `CreateRectRgn` función de miembro para evitar llamadas al administrador de memoria local.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)




