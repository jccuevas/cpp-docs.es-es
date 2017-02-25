---
title: "CRgn (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRgn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HRGN"
  - "CRgn (clase)"
  - "regiones de MFC"
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CRgn (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una región de la Interfaz de dispositivo gráfico (GDI) de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRgn : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRgn::CRgn](#crgn__crgn)|Construye un objeto `CRgn`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRgn::CombineRgn](#crgn__combinergn)|Establece un `CRgn` de objeto para que sea equivalente a la unión de dos especificado `CRgn` objetos.|  
|[CRgn::CopyRgn](#crgn__copyrgn)|Establece un `CRgn` de objeto para que sea una copia de un objeto `CRgn` objeto.|  
|[CRgn::CreateEllipticRgn](#crgn__createellipticrgn)|Inicializa un `CRgn` objeto con una región elíptica.|  
|[CRgn::CreateEllipticRgnIndirect](#crgn__createellipticrgnindirect)|Inicializa un `CRgn` objeto con una región elíptica definida por un [RECT](../../mfc/reference/rect-structure1.md) estructura.|  
|[CRgn::CreateFromData](#crgn__createfromdata)|Crea una región de los datos de transformación y región determinados.|  
|[CRgn::CreateFromPath](#crgn__createfrompath)|Crea una región de la ruta de acceso que se ha seleccionado en el contexto de dispositivo determinado.|  
|[CRgn::CreatePolygonRgn](#crgn__createpolygonrgn)|Inicializa un `CRgn` objeto con una región poligonal. El sistema cierra el polígono automáticamente, si es necesario, dibujando una línea desde el último vértice al primero.|  
|[CRgn::CreatePolyPolygonRgn](#crgn__createpolypolygonrgn)|Inicializa un `CRgn` objeto con una región que consta de una serie de polígonos cerrados. Los polígonos haya separado, o quizá se superpongan.|  
|[CRgn::CreateRectRgn](#crgn__createrectrgn)|Inicializa un `CRgn` objeto con una región rectangular.|  
|[CRgn::CreateRectRgnIndirect](#crgn__createrectrgnindirect)|Inicializa un `CRgn` objeto con una región rectangular definida por un [RECT](../../mfc/reference/rect-structure1.md) estructura.|  
|[CRgn::CreateRoundRectRgn](#crgn__createroundrectrgn)|Inicializa un `CRgn` objeto con una región rectangular con esquinas redondeadas.|  
|[CRgn::EqualRgn](#crgn__equalrgn)|Comprueba dos `CRgn` objetos para determinar si son equivalentes.|  
|[CRgn::FromHandle](#crgn__fromhandle)|Devuelve un puntero a un `CRgn` objeto cuando se especifica un identificador para una región de Windows.|  
|[CRgn::GetRegionData](#crgn__getregiondata)|Llena el búfer especificado con los datos que describen la región determinada.|  
|[CRgn::GetRgnBox](#crgn__getrgnbox)|Recupera las coordenadas del rectángulo delimitador de un `CRgn` objeto.|  
|[CRgn::OffsetRgn](#crgn__offsetrgn)|Mueve un `CRgn` objeto por los desplazamientos indicados.|  
|[CRgn::PtInRegion](#crgn__ptinregion)|Determina si un punto especificado está en la región.|  
|[CRgn::RectInRegion](#crgn__rectinregion)|Determina si cualquier parte de un rectángulo especificado está dentro de los límites de la región.|  
|[CRgn::SetRectRgn](#crgn__setrectrgn)|Establece la `CRgn` objeto en la región rectangular especificada.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRgn::operator HRGN](#crgn__operator_hrgn)|Devuelve el identificador de Windows incluido en la `CRgn` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Una región es un área poligonal o elíptico dentro de una ventana. Para usar regiones, usa las funciones miembro de clase `CRgn` con las funciones de recorte definidas como miembros de la clase `CDC`.  
  
 Las funciones miembro de `CRgn` crear, modificar y recuperar información sobre el objeto de región para el que se llama.  
  
 Para obtener más información sobre el uso de `CRgn`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecrgncombinergna-crgncombinergn"></a><a name="crgn__combinergn"></a>  CRgn::CombineRgn  
 Crea una nueva área GDI mediante la combinación de dos regiones existentes.  
  
```  
int CombineRgn(
    CRgn* pRgn1,  
    CRgn* pRgn2,  
    int nCombineMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn1`  
 Identifica una región existente.  
  
 `pRgn2`  
 Identifica una región existente.  
  
 `nCombineMode`  
 Especifica la operación que se realizará cuando se combinan las regiones de origen de dos. Puede ser cualquiera de los siguientes valores:  
  
- **RGN_AND** usa las áreas superpuestas de ambas regiones (intersección).  
  
- **RGN_COPY** crea una copia de la región 1 (identificado por `pRgn1`).  
  
- **RGN_DIFF** crea una región que consta de las áreas de la región 1 (identificado por `pRgn1`) que no forman parte de la región 2 (identificado por `pRgn2`).  
  
- **RGN_OR** combina ambas regiones en su totalidad (unión).  
  
- **RGN_XOR** combina ambas regiones pero quita las áreas superpuestas.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:  
  
- **COMPLEXREGION** nueva región tiene bordes se superponen.  
  
- **ERROR** ninguna región nuevo creada.  
  
- **NULLREGION** nueva región está vacía.  
  
- **SIMPLEREGION** nueva región no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 Las regiones se combinan según se especifica en `nCombineMode`.  
  
 Los dos especificados se combinan las regiones y el identificador de región resultante se almacena en la `CRgn` objeto. Por lo tanto, cualquier región se almacena en la `CRgn` objeto se reemplaza por la región combinada.  
  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Utilice [CopyRgn](#crgn__copyrgn) simplemente para copiar una región en otra región.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/CPP/crgn-class_1.cpp)]  
  
##  <a name="a-namecrgncopyrgna-crgncopyrgn"></a><a name="crgn__copyrgn"></a>  CRgn::CopyRgn  
 Copia la región definida por `pRgnSrc` en la `CRgn` objeto.  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgnSrc`  
 Identifica una región existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el tipo de la región resultante. Puede ser uno de los siguientes valores:  
  
- **COMPLEXREGION** nueva región tiene bordes se superponen.  
  
- **ERROR** ninguna región nuevo creada.  
  
- **NULLREGION** nueva región está vacía.  
  
- **SIMPLEREGION** nueva región no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 La nueva región reemplaza la región almacenada anteriormente en el `CRgn` objeto. Esta función es un caso especial de la [CombineRgn](#crgn__combinergn) función miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateEllipticRgn](#crgn__createellipticrgn).  
  
##  <a name="a-namecrgncreateellipticrgna-crgncreateellipticrgn"></a><a name="crgn__createellipticrgn"></a>  CRgn::CreateEllipticRgn  
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
 Distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La región se define por el rectángulo delimitador especificado por `x1`, `y1`, `x2`, y `y2`. La región se almacena en la `CRgn` objeto.  
  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Cuando ha terminado de usar una región creada con el `CreateEllipticRgn` función, una aplicación debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitarlo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/CPP/crgn-class_2.cpp)]  
  
##  <a name="a-namecrgncreateellipticrgnindirecta-crgncreateellipticrgnindirect"></a><a name="crgn__createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect  
 Crea una región elíptica.  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `RECT` estructura o un `CRect` objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha del rectángulo delimitador de la elipse.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La región se define mediante la estructura o el objeto al que señala `lpRect` y se almacena en la `CRgn` objeto.  
  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Cuando ha terminado de usar una región creada con el `CreateEllipticRgnIndirect` función, una aplicación debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitarlo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateRectRgnIndirect](#crgn__createrectrgnindirect).  
  
##  <a name="a-namecrgncreatefromdataa-crgncreatefromdata"></a><a name="crgn__createfromdata"></a>  CRgn::CreateFromData  
 Crea una región de los datos de transformación y región determinados.  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpXForm*  
 Apunta a un [XFORM](../../mfc/reference/xform-structure.md) estructura de datos que define la transformación que se realizará en la región. Si este puntero es **NULL**, se usa la transformación de identidad.  
  
 `nCount`  
 Especifica el número de bytes que apunta `pRgnData`.  
  
 `pRgnData`  
 Apunta a un [RGNDATA](../../mfc/reference/rgndata-structure.md) estructura de datos que contiene los datos de la región.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación puede recuperar datos de una región llamando el `CRgn::GetRegionData` (función).  
  
##  <a name="a-namecrgncreatefrompatha-crgncreatefrompath"></a><a name="crgn__createfrompath"></a>  CRgn::CreateFromPath  
 Crea una región de la ruta de acceso que se ha seleccionado en el contexto de dispositivo determinado.  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Identifica un contexto de dispositivo que contiene un trayecto cerrado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de dispositivo identificado por el `pDC` parámetro debe contener un trayecto cerrado. Después de `CreateFromPath` convierte una ruta de acceso en una región, Windows descarta la ruta cerrada desde el contexto de dispositivo.  
  
##  <a name="a-namecrgncreatepolygonrgna-crgncreatepolygonrgn"></a><a name="crgn__createpolygonrgn"></a>  CRgn::CreatePolygonRgn  
 Crea una región poligonal.  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de **PUNTO** estructuras o una matriz de `CPoint` objetos. Cada estructura especifica la coordenada x y Coordenada y de un vértice del polígono. El **PUNTO** estructura tiene el formato siguiente:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `nCount`  
 Especifica el número de **PUNTO** estructuras o `CPoint` objetos de la matriz señalada por `lpPoints`.  
  
 `nMode`  
 Especifica el modo de relleno para la región. Este parámetro puede ser **ALTERNATIVO** o **DEVANADO**.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El sistema cierra el polígono automáticamente, si es necesario, dibujando una línea desde el último vértice al primero. La región resultante se almacena en la `CRgn` objeto.  
  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Cuando el modo de relleno de polígono es **ALTERNATIVO**, el sistema rellena el área entre los lados de un polígono pares e impares en cada línea de exploración. Es decir, el sistema rellena el área entre la primera y segunda parte, entre el lado tercero y cuarto y así sucesivamente.  
  
 Cuando el modo de relleno de polígono es **DEVANADO**, el sistema usa la dirección en la que se dibuja una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en un hacia la derecha o una dirección a la izquierda. Siempre que una línea imaginaria de un área delimitada al exterior de una figura pasa a través de un segmento de línea de las agujas del reloj, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea a la izquierda, el recuento es reducido. El área se rellena si el recuento es distinto de cero cuando llega a la línea de la parte exterior de la figura.  
  
 Cuando una aplicación ha terminado de usar una región creada con el `CreatePolygonRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la `DeleteObject` función para quitarlo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/CPP/crgn-class_3.cpp)]  
  
##  <a name="a-namecrgncreatepolypolygonrgna-crgncreatepolypolygonrgn"></a><a name="crgn__createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn  
 Crea una región formada por una serie de polígonos cerrados.  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de **PUNTO** estructuras o una matriz de `CPoint` objetos que define los vértices de los polígonos. Cada polígono se debe cerrar explícitamente porque el sistema no cierre automáticamente. Los polígonos se especifican de forma consecutiva. El **PUNTO** estructura tiene el formato siguiente:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `lpPolyCounts`  
 Apunta a una matriz de enteros. El primer entero especifica el número de vértices en el primer polígono en la `lpPoints` matriz, el segundo entero especifica el número de vértices en el polígono segundo y así sucesivamente.  
  
 `nCount`  
 Especifica el número total de enteros en la `lpPolyCounts` matriz.  
  
 `nPolyFillMode`  
 Especifica el modo de relleno de polígono. Este valor puede ser **ALTERNATIVO** o **DEVANADO**.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La región resultante se almacena en la `CRgn` objeto.  
  
 Los polígonos haya separado, o quizá se superpongan.  
  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Cuando el modo de relleno de polígono es **ALTERNATIVO**, el sistema rellena el área entre los lados de un polígono pares e impares en cada línea de exploración. Es decir, el sistema rellena el área entre la primera y segunda parte, entre el lado tercero y cuarto y así sucesivamente.  
  
 Cuando el modo de relleno de polígono es **DEVANADO**, el sistema usa la dirección en la que se dibuja una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en un hacia la derecha o una dirección a la izquierda. Siempre que una línea imaginaria de un área delimitada al exterior de una figura pasa a través de un segmento de línea de las agujas del reloj, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea a la izquierda, el recuento es reducido. El área se rellena si el recuento es distinto de cero cuando llega a la línea de la parte exterior de la figura.  
  
 Cuando una aplicación ha terminado de usar una región creada con el `CreatePolyPolygonRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) función miembro para quitarlo.  
  
##  <a name="a-namecrgncreaterectrgna-crgncreaterectrgn"></a><a name="crgn__createrectrgn"></a>  CRgn::CreateRectRgn  
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
 Distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Cuando ha terminado de usar una región creada por `CreateRectRgn`, una aplicación debe utilizar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) función miembro para quitar la región.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/CPP/crgn-class_4.cpp)]  
  
 Para obtener otro ejemplo, vea [CRgn::CombineRgn](#crgn__combinergn).  
  
##  <a name="a-namecrgncreaterectrgnindirecta-crgncreaterectrgnindirect"></a><a name="crgn__createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect  
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
 Distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Cuando ha terminado de usar una región creada por `CreateRectRgnIndirect`, una aplicación debe utilizar el [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) función miembro para quitar la región.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/CPP/crgn-class_5.cpp)]  
  
##  <a name="a-namecrgncreateroundrectrgna-crgncreateroundrectrgn"></a><a name="crgn__createroundrectrgn"></a>  CRgn::CreateRoundRectRgn  
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
 Distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de una región está limitado a 32.767 por 32.767 las unidades lógicas o de 64 KB de memoria, lo que sea menor.  
  
 Cuando una aplicación ha terminado de usar una región creada con el `CreateRoundRectRgn` función, debe seleccionar la región fuera del contexto de dispositivo y utilice la [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) función miembro para quitarlo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/CPP/crgn-class_6.cpp)]  
  
##  <a name="a-namecrgncrgna-crgncrgn"></a><a name="crgn__crgn"></a>  CRgn::CRgn  
 Construye un objeto `CRgn`.  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_hObject` miembro de datos no contiene una región de GDI de Windows válida hasta que se inicializa el objeto con uno o varios de los demás `CRgn` funciones miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateRoundRectRgn](#crgn__createroundrectrgn).  
  
##  <a name="a-namecrgnequalrgna-crgnequalrgn"></a><a name="crgn__equalrgn"></a>  CRgn::EqualRgn  
 Determina si la región determinada es equivalente a la región que se almacenan en la `CRgn` objeto.  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Identifica una región.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si las dos regiones son equivalentes; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/CPP/crgn-class_7.cpp)]  
  
##  <a name="a-namecrgnfromhandlea-crgnfromhandle"></a><a name="crgn__fromhandle"></a>  CRgn::FromHandle  
 Devuelve un puntero a un `CRgn` objeto cuando se especifica un identificador para una región de Windows.  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>Parámetros  
 `hRgn`  
 Especifica un identificador de una región de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CRgn` objeto. Si la función no se realizó correctamente, el valor devuelto es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CRgn` objeto no está asociado al identificador de un objeto temporal `CRgn` objeto creado y conectado. Este temporal `CRgn` objeto es válido sólo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal de todos los objetos se eliminan. Otra forma de decir esto es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
##  <a name="a-namecrgngetregiondataa-crgngetregiondata"></a><a name="crgn__getregiondata"></a>  CRgn::GetRegionData  
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
 Estos datos incluyen las dimensiones de los rectángulos que componen la región. Esta función se utiliza junto con el `CRgn::CreateFromData` (función).  
  
##  <a name="a-namecrgngetrgnboxa-crgngetrgnbox"></a><a name="crgn__getrgnbox"></a>  CRgn::GetRgnBox  
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
 Especifica el tipo de región. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** región tiene bordes se superponen.  
  
- **NULLREGION** región está vacía.  
  
- **ERROR** `CRgn` el objeto no especifica una región válida.  
  
- **SIMPLEREGION** región no tiene bordes superpuestos.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreatePolygonRgn](#crgn__createpolygonrgn).  
  
##  <a name="a-namecrgnoffsetrgna-crgnoffsetrgn"></a><a name="crgn__offsetrgn"></a>  CRgn::OffsetRgn  
 Mueve la región que se almacenan en la `CRgn` objeto por los desplazamientos indicados.  
  
```  
int OffsetRgn(
    int x,  
    int y);

 
int OffsetRgn(
    POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica el número de unidades para mover a la izquierda o derecha.  
  
 *y*  
 Especifica el número de unidades para mover hacia arriba o hacia abajo.  
  
 `point`  
 La coordenada x de `point` especifica el número de unidades para mover a la izquierda o derecha. La coordenada y de `point` especifica el número de unidades para mover hacia arriba o hacia abajo. El `point` parámetro puede ser un **PUNTO** estructura o un `CPoint` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de la nueva región. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** región tiene bordes se superponen.  
  
- **ERROR** identificador de región no es válido.  
  
- **NULLREGION** región está vacía.  
  
- **SIMPLEREGION** región no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 La función mueve a la región *x* unidades a lo largo del eje x y *y* unidades a lo largo del eje y.  
  
 Los valores de coordenadas de una región deben ser menor o igual que 32.767 y mayor o igual a -32.768. El *x* y *y* parámetros se deben elegir con cuidado para evitar que las coordenadas de región no válido.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateEllipticRgn](#crgn__createellipticrgn).  
  
##  <a name="a-namecrgnoperatorhrgna-crgnoperator-hrgn"></a><a name="crgn__operator_hrgn"></a>  CRgn::operator HRGN  
 Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CRgn` objeto.  
  
''' operador HRGN() const;

 
```  
  
### Return Value  
 If successful, a handle to the Windows GDI object represented by the `CRgn` object; otherwise **NULL**.  
  
### Remarks  
 This operator is a casting operator, which supports direct use of an **HRGN** object.  
  
 For more information about using graphic objects, see the article [Graphic Objects](http://msdn.microsoft.com/library/windows/desktop/dd144962) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="crgn__ptinregion"></a>  CRgn::PtInRegion  
 Checks whether the point given by *x* and *y* is in the region stored in the `CRgn` object.  
  
```  
BOOL PtInRegion (int x,  
    int y) const;

 
 
BOOL PtInRegion (punto) const;

 
```  
  
### Parameters  
 *x*  
 Specifies the logical x-coordinate of the point to test.  
  
 *y*  
 Specifies the logical y-coordinate of the point to test.  
  
 `point`  
 The x- and y-coordinates of `point` specify the x- and y-coordinates of the point to test the value of. The `point` parameter can either be a **POINT** structure or a `CPoint` object.  
  
### Return Value  
 Nonzero if the point is in the region; otherwise 0.  
  
##  <a name="crgn__rectinregion"></a>  CRgn::RectInRegion  
 Determines whether any part of the rectangle specified by `lpRect` is within the boundaries of the region stored in the `CRgn` object.  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;

 
```  
  
### Parameters  
 `lpRect`  
 Points to a `RECT` structure or `CRect` object. The `RECT` structure has the following form:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### Return Value  
 Nonzero if any part of the specified rectangle lies within the boundaries of the region; otherwise 0.  
  
##  <a name="crgn__setrectrgn"></a>  CRgn::SetRectRgn  
 Creates a rectangular region.  
  
```  
void SetRectRgn (int x1,  
    y1 int,  
    int x2,  
    int y2);

 
void SetRectRgn (LPCRECT lpRect);
```  
  
### Parameters  
 `x1`  
 Specifies the x-coordinate of the upper-left corner of the rectangular region.  
  
 `y1`  
 Specifies the y-coordinate of the upper-left corner of the rectangular region.  
  
 `x2`  
 Specifies the x-coordinate of the lower-right corner of the rectangular region.  
  
 `y2`  
 Specifies the y-coordinate of the lower-right corner of the rectangular region.  
  
 `lpRect`  
 Specifies the rectangular region. Can be either a pointer to a `RECT` structure or a `CRect` object.  
  
### Remarks  
 Unlike [CreateRectRgn](#crgn__createrectrgn), however, it does not allocate any additional memory from the local Windows application heap. Instead, it uses the space allocated for the region stored in the `CRgn` object. This means that the `CRgn` object must already have been initialized with a valid Windows region before calling `SetRectRgn`. The points given by `x1`, `y1`, `x2`, and `y2` specify the minimum size of the allocated space.  
  
 Use this function instead of the `CreateRectRgn` member function to avoid calls to the local memory manager.  
  
## See Also  
 [CWnd Class](../../mfc/reference/cwnd-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)



