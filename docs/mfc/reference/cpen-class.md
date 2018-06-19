---
title: CPen (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
dev_langs:
- C++
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 995e3f85ec21cae1be18f0bf7b6548c912ca5254
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376384"
---
# <a name="cpen-class"></a>CPen (clase)
Encapsula un lápiz de la Interfaz de dispositivo gráfico (GDI) de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPen : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPen::CPen](#cpen)|Construye un objeto `CPen`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPen::CreatePen](#createpen)|Crea un lápiz cosmético o geométrico lógico con el estilo especificado, el ancho y el pincel atributos y se adjunta a la `CPen` objeto.|  
|[CPen::CreatePenIndirect](#createpenindirect)|Crea un lápiz con el estilo, ancho y color de un [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) de la estructura y se adjunta a la `CPen` objeto.|  
|[CPen::FromHandle](#fromhandle)|Devuelve un puntero a un `CPen` objeto cuando se especifica una ventana `HPEN`.|  
|[CPen::GetExtLogPen](#getextlogpen)|Obtiene un [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) estructura subyacente.|  
|[CPen::GetLogPen](#getlogpen)|Obtiene un [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) estructura subyacente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPen::operator HPEN](#operator_hpen)|Devuelve el identificador de Windows asociado a la `CPen` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el uso de `CPen`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cpen"></a>  CPen::CPen  
 Construye un objeto `CPen`.  
  
```  
CPen();

 
CPen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
CPen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPenStyle`  
 Especifica el estilo de lápiz. Este parámetro en la primera versión del constructor puede ser uno de los siguientes valores:  
  
- **PS_SOLID** crea un lápiz sólido.  
  
- **PS_DASH** crea un lápiz discontinuo. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_DOT** crea un lápiz con puntos. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_DASHDOT** crea un lápiz con guiones y puntos alternativamente. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_DASHDOTDOT** crea un lápiz con guiones y puntos dobles alternos. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_NULL** crea un lápiz null.  
  
- **PS_INSIDEFRAME** crea un lápiz que dibuja una línea dentro del marco de las formas cerradas generados por las funciones de salida de GDI de Windows que especifican un rectángulo delimitador (por ejemplo, el **elipse**, **rectángulo** , `RoundRect`, `Pie`, y `Chord` funciones miembro). Cuando se utiliza este estilo con funciones de salida de GDI de Windows que no especifican un rectángulo delimitador (por ejemplo, el `LineTo` función miembro), el área de dibujo del lápiz no está limitado por un marco.  
  
 La segunda versión de la `CPen` constructor especifica una combinación de tipo, estilo, extremo y atributos de combinación. Los valores de cada categoría deben combinarse mediante el operador OR bit a bit (&#124;). El tipo de lápiz puede ser uno de los valores siguientes:  
  
- **PS_GEOMETRIC** crea un lápiz geométrico.  
  
- **PS_COSMETIC** crea un lápiz cosmético.  
  
     La segunda versión de la `CPen` constructor agrega los siguientes estilos de lápiz para `nPenStyle`:  
  
- **PS_ALTERNATE** crea un lápiz que establece todos los demás píxeles. (Este estilo sólo es aplicable para lápices cosméticos.)  
  
- **PS_USERSTYLE** crea un lápiz que usa una matriz de estilo suministrada por el usuario.  
  
     El extremo puede ser uno de los siguientes valores:  
  
- **PS_ENDCAP_ROUND** extremos son round.  
  
- **PS_ENDCAP_SQUARE** extremos son cuadrados.  
  
- **PS_ENDCAP_FLAT** extremos son planos.  
  
     La combinación puede ser uno de los siguientes valores:  
  
- **PS_JOIN_BEVEL** se biselado combinaciones.  
  
- **PS_JOIN_MITER** combinaciones son ángulo cuando están en el límite actual establecido por la [SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076) (función). Si la combinación supera este límite, se biselado.  
  
- **PS_JOIN_ROUND** combinaciones son round.  
  
 `nWidth`  
 Especifica el ancho del lápiz.  
  
-   Para la primera versión del constructor, si este valor es 0, el ancho en unidades del dispositivo siempre es 1 píxel, independientemente del modo de asignación.  
  
-   Para la segunda versión del constructor, si `nPenStyle` es **PS_GEOMETRIC**, el ancho se expresa en unidades lógicas. Si `nPenStyle` es **PS_COSMETIC**, el ancho debe establecerse en 1.  
  
 `crColor`  
 Contiene un color RGB para el lápiz.  
  
 `pLogBrush`  
 Apunta a un `LOGBRUSH` estructura. Si `nPenStyle` es **PS_COSMETIC**, el `lbColor` miembro de la `LOGBRUSH` estructura especifica el color del lápiz y el `lbStyle` miembro de la `LOGBRUSH` estructura debe establecerse en **BS_ SÓLIDO**. Si `nPenStyle` es **PS_GEOMETRIC**, todos los miembros deben utilizarse para especificar los atributos de pincel del lápiz.  
  
 `nStyleCount`  
 Especifica la longitud, en unidades de palabra doble, de la `lpStyle` matriz. Este valor debe ser cero si `nPenStyle` no **PS_USERSTYLE**.  
  
 `lpStyle`  
 Apunta a una matriz de valores de palabra doble. El primer valor especifica la longitud de la primera guión en un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio y así sucesivamente. This (puntero) debe ser **NULL** si `nPenStyle` no **PS_USERSTYLE**.  
  
### <a name="remarks"></a>Comentarios  
 Si utiliza el constructor sin argumentos, debe inicializar resultante `CPen` objeto con el `CreatePen`, `CreatePenIndirect`, o `CreateStockObject` funciones miembro.  
  
 Si utiliza el constructor que toma argumentos, ninguna inicialización adicional es necesaria. El constructor con argumentos puede producir una excepción si se encuentran errores, mientras que el constructor sin argumentos siempre se realizará correctamente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>  CPen::CreatePen  
 Crea un lápiz cosmético o geométrico lógico con el estilo especificado, el ancho y el pincel atributos y se adjunta a la `CPen` objeto.  
  
```  
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPenStyle`  
 Especifica el estilo del lápiz. Para obtener una lista de valores posibles, vea el `nPenStyle` parámetro en el [CPen](#cpen) constructor.  
  
 `nWidth`  
 Especifica el ancho del lápiz.  
  
-   Para la primera versión de `CreatePen`, si este valor es 0, el ancho en unidades del dispositivo siempre es 1 píxel, independientemente del modo de asignación.  
  
-   Para la segunda versión de `CreatePen`si `nPenStyle` es **PS_GEOMETRIC**, el ancho se expresa en unidades lógicas. Si `nPenStyle` es **PS_COSMETIC**, el ancho debe establecerse en 1.  
  
 `crColor`  
 Contiene un color RGB para el lápiz.  
  
 `pLogBrush`  
 Apunta a un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura. Si `nPenStyle` es **PS_COSMETIC**, el **lbColor** miembro de la `LOGBRUSH` estructura especifica el color del lápiz y el `lbStyle` miembro de la `LOGBRUSH` estructura debe ser establecido en **BS_SOLID**. Si **nPenStyle** es **PS_GEOMETRIC**, todos los miembros deben utilizarse para especificar los atributos de pincel del lápiz.  
  
 `nStyleCount`  
 Especifica la longitud, en unidades de palabra doble, de la `lpStyle` matriz. Este valor debe ser cero si `nPenStyle` no **PS_USERSTYLE**.  
  
 `lpStyle`  
 Apunta a una matriz de valores de palabra doble. El primer valor especifica la longitud de la primera guión en un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio y así sucesivamente. This (puntero) debe ser **NULL** si `nPenStyle` no **PS_USERSTYLE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, o cero si se produce un error en el método.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión de `CreatePen` Inicializa un lápiz con el estilo especificado, el ancho y el color. El lápiz puede seleccionarse posteriormente como el lápiz actual para cualquier contexto de dispositivo.  
  
 Lápices que tienen un ancho mayor que 1 píxel siempre debe tener la **PS_NULL**, **PS_SOLID**, o **PS_INSIDEFRAME** estilo.  
  
 Si tiene un lápiz el **PS_INSIDEFRAME** estilo y un color que no coincide con un color en la tabla de colores lógica, se dibuja el lápiz con un color interpolado. El **PS_SOLID** estilo del lápiz no se puede usar para crear un lápiz con un color interpolado. El estilo **PS_INSIDEFRAME** es idéntico a **PS_SOLID** si el ancho del lápiz es menor o igual que 1.  
  
 La segunda versión de `CreatePen` Inicializa un lápiz cosmético o geométrico lógico que tenga especificado el estilo, ancho y atributos del pincel. El ancho de un lápiz cosmético siempre es 1; el ancho de un lápiz geométrico siempre se especifica en unidades universales. Después de que una aplicación crea un lápiz lógico, puede seleccionar ese lápiz en un contexto de dispositivo mediante una llamada a la [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) función. Después de selecciona un lápiz en un contexto de dispositivo, se puede utilizar para dibujar líneas y curvas conectadas.  
  
-   Si `nPenStyle` es **PS_COSMETIC** y **PS_USERSTYLE**, las entradas de la `lpStyle` matriz especificar longitudes de guiones y espacios en unidades de estilo. Una unidad de estilo se define mediante el dispositivo en el que se usa el lápiz para dibujar una línea.  
  
-   Si `nPenStyle` es **PS_GEOMETRIC** y **PS_USERSTYLE**, las entradas de la `lpStyle` matriz especificar longitudes de guiones y espacios en unidades lógicas.  
  
-   Si `nPenStyle` es **PS_ALTERNATE**, la unidad de estilo se omite y se establece todos los demás píxeles.  
  
 Cuando una aplicación ya no requiere un lápiz determinado, debe llamar a la [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) miembro de función o destruir la `CPen` del objeto para el recurso ya no está en uso. Una aplicación no debe eliminar un lápiz cuando el lápiz está seleccionado en un contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect  
 Inicializa un lápiz que tiene el estilo, ancho y color proporcionado en la estructura que señala `lpLogPen`.  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpLogPen`  
 Apunta a las ventanas [LOGPEN](../../mfc/reference/logpen-structure.md) estructura que contiene información sobre el lápiz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Lápices que tienen un ancho mayor que 1 píxel siempre debe tener la **PS_NULL**, **PS_SOLID**, o **PS_INSIDEFRAME** estilo.  
  
 Si tiene un lápiz el **PS_INSIDEFRAME** estilo y un color que no coincide con un color en la tabla de colores lógica, se dibuja el lápiz con un color interpolado. El **PS_INSIDEFRAME** estilo es idéntico a **PS_SOLID** si el ancho del lápiz es menor o igual que 1.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>  CPen::FromHandle  
 Devuelve un puntero a un `CPen` objeto especifica un identificador a un objeto de lápiz GDI de Windows.  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>Parámetros  
 *hPen*  
 `HPEN` identificador de lápiz GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CPen` objeto si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay un objeto `CPen` asociado al identificador, se crea y asocia un objeto `CPen` temporal. Este temporal `CPen` objeto es válido solo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal todos los objetos se eliminan. En otras palabras, el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>  CPen::GetExtLogPen  
 Obtiene un **EXTLOGPEN** estructura subyacente.  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLogPen`  
 Apunta a un [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) estructura que contiene información sobre el lápiz.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El **EXTLOGPEN** estructura define el estilo, ancho y atributos de pincel de un lápiz. Por ejemplo, llamar a `GetExtLogPen` para que coincida con el estilo determinado de un lápiz.  
  
 Vea los temas siguientes en el SDK de Windows para obtener información acerca de los atributos de lápiz:  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente se muestra cómo llamar `GetExtLogPen` para recuperar los atributos del lápiz y, a continuación, crear un lápiz cosmético, nueva con el mismo color.  
  
 [!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>  CPen::GetLogPen  
 Obtiene un `LOGPEN` estructura subyacente.  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLogPen`  
 Apunta a un [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) estructura para contener información sobre el lápiz.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El `LOGPEN` estructura define el estilo, el color y el patrón de un lápiz.  
  
 Por ejemplo, llamar a `GetLogPen` para que coincida con el estilo determinado de lápiz.  
  
 Vea los temas siguientes en el SDK de Windows para obtener información acerca de los atributos de lápiz:  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente se muestra cómo llamar `GetLogPen` para recuperar un carácter de lápiz y, a continuación, crear un lápiz sólido, nueva con el mismo color.  
  
 [!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>  CPen::operator HPEN  
 Obtiene el identificador de GDI de Windows asociado de la `CPen` objeto.  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto GDI de Windows representado por la `CPen` objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Éste es un operador de conversión, que admite el uso directo de un `HPEN` objeto.  
  
 Para obtener más información sobre el uso de objetos gráficos, vea el artículo [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CBrush (clase)](../../mfc/reference/cbrush-class.md)
