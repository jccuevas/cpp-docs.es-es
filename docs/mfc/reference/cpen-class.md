---
title: CPen (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- HPEN
- CPen class
- pens, MFC
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: edea12c84a8f39161acbf367360fd86a1ff19998
ms.lasthandoff: 02/24/2017

---
# <a name="cpen-class"></a>CPen (clase)
Encapsula un lápiz de la Interfaz de dispositivo gráfico (GDI) de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPen : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPen::CPen](#cpen)|Construye un objeto `CPen`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPen::CreatePen](#createpen)|Crea un lápiz cosmético o geométrico lógico con el estilo especificado, el ancho y el pincel atributos y se adjunta a la `CPen` objeto.|  
|[CPen::CreatePenIndirect](#createpenindirect)|Crea un lápiz con el estilo, ancho y color de una [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) estructura y se adjunta a la `CPen` objeto.|  
|[CPen::FromHandle](#fromhandle)|Devuelve un puntero a un `CPen` objeto cuando se especifica un Windows `HPEN`.|  
|[CPen::GetExtLogPen](#getextlogpen)|Obtiene un [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) estructura subyacente.|  
|[CPen::GetLogPen](#getlogpen)|Obtiene un [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) estructura subyacente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
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
  
##  <a name="cpen"></a>CPen::CPen  
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
 Especifica el estilo del lápiz. Este parámetro en la primera versión del constructor puede ser uno de los siguientes valores:  
  
- **PS_SOLID** crea un lápiz sólido.  
  
- **PS_DASH** crea un lápiz rayado. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_DOT** crea un lápiz con puntos. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_DASHDOT** crea un lápiz con guiones y puntos alternativamente. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_DASHDOTDOT** crea un lápiz con guiones y puntos dobles alternos. Sólo es válido cuando el ancho del lápiz es unidades de 1 o menos, en el dispositivo.  
  
- **PS_NULL** crea un lápiz null.  
  
- **PS_INSIDEFRAME** crea un lápiz que dibuja una línea dentro del marco de las formas cerradas producidos por las funciones de salida de Windows GDI que especifican un rectángulo delimitador (por ejemplo, el **elipse**, **rectángulo**, `RoundRect`, `Pie`, y `Chord` funciones miembro). Cuando se utiliza este estilo con funciones de salida de GDI de Windows que no especifican un rectángulo delimitador (por ejemplo, el `LineTo` función miembro), el área de dibujo del lápiz no está limitado por un marco.  
  
 La segunda versión de la `CPen` constructor especifica una combinación de tipo, estilo, extremo y atributos de combinación. Los valores de cada categoría deben combinarse mediante el operador OR bit a bit (|). El tipo de lápiz puede ser uno de los siguientes valores:  
  
- **PS_GEOMETRIC** crea un lápiz geométrico.  
  
- **PS_COSMETIC** crea un lápiz cosmético.  
  
     La segunda versión de la `CPen` constructor agrega los siguientes estilos de lápiz para `nPenStyle`:  
  
- **PS_ALTERNATE** crea un lápiz que establece todos los demás píxeles. (Este estilo solo es aplicable de lápices cosméticas.)  
  
- **PS_USERSTYLE** crea un lápiz que usa una matriz de estilo proporcionada por el usuario.  
  
     El extremo puede ser uno de los siguientes valores:  
  
- **PS_ENDCAP_ROUND** extremos son round.  
  
- **PS_ENDCAP_SQUARE** extremos son cuadrados.  
  
- **PS_ENDCAP_FLAT** extremos son planos.  
  
     La combinación puede ser uno de los siguientes valores:  
  
- **PS_JOIN_BEVEL** se biselado combinaciones.  
  
- **PS_JOIN_MITER** combinaciones son ángulo cuando estén dentro del límite actual establecido por el [SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076) (función). Si la combinación supera este límite, se biselado.  
  
- **PS_JOIN_ROUND** combinaciones son round.  
  
 `nWidth`  
 Especifica el ancho del lápiz.  
  
-   Para la primera versión del constructor, si este valor es 0, el ancho, en unidades del dispositivo siempre es 1 píxel, independientemente del modo de asignación.  
  
-   Para la segunda versión del constructor, si `nPenStyle` es **PS_GEOMETRIC**, el ancho se expresa en unidades lógicas. Si `nPenStyle` es **PS_COSMETIC**, el ancho se debe establecer en 1.  
  
 `crColor`  
 Contiene un color RGB para el lápiz.  
  
 `pLogBrush`  
 Apunta a un `LOGBRUSH` estructura. Si `nPenStyle` es **PS_COSMETIC**, el `lbColor` miembro de la `LOGBRUSH` estructura especifica el color del lápiz y el `lbStyle` miembro de la `LOGBRUSH` estructura debe establecerse en **BS_SOLID**. Si `nPenStyle` es **PS_GEOMETRIC**, todos los miembros que deben usarse para especificar los atributos de pincel del lápiz.  
  
 `nStyleCount`  
 Especifica la longitud en unidades de palabra doble, de la `lpStyle` matriz. Este valor debe ser cero si `nPenStyle` no **PS_USERSTYLE**.  
  
 `lpStyle`  
 Apunta a una matriz de valores de palabra doble. El primer valor especifica la longitud del primer guión en un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio y así sucesivamente. This (puntero) debe ser **NULL** si `nPenStyle` no **PS_USERSTYLE**.  
  
### <a name="remarks"></a>Comentarios  
 Si utiliza el constructor sin argumentos, debe inicializar resultante `CPen` objeto con el `CreatePen`, `CreatePenIndirect`, o `CreateStockObject` funciones miembro.  
  
 Si utiliza el constructor que toma argumentos, ninguna inicialización adicional es necesaria. El constructor con argumentos puede producir una excepción si se producen errores, mientras que el constructor sin argumentos siempre se realizará correctamente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#99;](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>CPen::CreatePen  
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
  
-   Para la primera versión de `CreatePen`, si este valor es 0, el ancho, en unidades del dispositivo siempre es 1 píxel, independientemente del modo de asignación.  
  
-   Para la segunda versión de `CreatePen`si `nPenStyle` es **PS_GEOMETRIC**, el ancho se expresa en unidades lógicas. Si `nPenStyle` es **PS_COSMETIC**, el ancho se debe establecer en 1.  
  
 `crColor`  
 Contiene un color RGB para el lápiz.  
  
 `pLogBrush`  
 Apunta a un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura. Si `nPenStyle` es **PS_COSMETIC**, el **lbColor** miembro de la `LOGBRUSH` estructura especifica el color del lápiz y el `lbStyle` miembro de la `LOGBRUSH` estructura debe establecerse en **BS_SOLID**. Si **nPenStyle** es **PS_GEOMETRIC**, todos los miembros que deben usarse para especificar los atributos de pincel del lápiz.  
  
 `nStyleCount`  
 Especifica la longitud en unidades de palabra doble, de la `lpStyle` matriz. Este valor debe ser cero si `nPenStyle` no **PS_USERSTYLE**.  
  
 `lpStyle`  
 Apunta a una matriz de valores de palabra doble. El primer valor especifica la longitud del primer guión en un estilo definido por el usuario, el segundo valor especifica la longitud del primer espacio y así sucesivamente. This (puntero) debe ser **NULL** si `nPenStyle` no **PS_USERSTYLE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, o cero si se produce un error en el método.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión de `CreatePen` Inicializa un lápiz con el estilo especificado, el ancho y el color. El lápiz puede seleccionarse posteriormente como el lápiz actual para cualquier contexto de dispositivo.  
  
 Lápices con un ancho superior a 1 píxel siempre debe tener ya sea la **PS_NULL**, **PS_SOLID**, o **PS_INSIDEFRAME** estilo.  
  
 Si tiene un lápiz la **PS_INSIDEFRAME** estilo y un color que no coincide con un color en la tabla de colores lógica, se dibuja el lápiz con un color interpolado. El **PS_SOLID** no se puede usar el estilo de pluma para crear un lápiz con un color interpolado. El estilo **PS_INSIDEFRAME** es idéntico a **PS_SOLID** si el ancho del lápiz es menor o igual que 1.  
  
 La segunda versión de `CreatePen` Inicializa un lápiz cosmético o geométrico lógico que tiene el estilo, ancho y atributos del pincel especificados. El ancho de un lápiz cosmético siempre es 1; el ancho de un lápiz geométrico siempre se especifica en unidades universales. Cuando una aplicación crea un lápiz lógico, puede seleccionar ese lápiz en un contexto de dispositivo llamando a la [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) (función). Después de seleccionar un lápiz en un contexto de dispositivo, puede usar para dibujar líneas y curvas.  
  
-   Si `nPenStyle` es **PS_COSMETIC** y **PS_USERSTYLE**, las entradas de la `lpStyle` matriz especificar longitud de guiones y espacios en unidades de estilo. Una unidad de estilo se define por el dispositivo en el que se usa el lápiz para dibujar una línea.  
  
-   Si `nPenStyle` es **PS_GEOMETRIC** y **PS_USERSTYLE**, las entradas de la `lpStyle` matriz especificar longitud de guiones y espacios en unidades lógicas.  
  
-   Si `nPenStyle` es **PS_ALTERNATE**, se omite la unidad de estilo y se establece todos los demás píxeles.  
  
 Cuando una aplicación ya no requiere un lápiz determinado, debe llamar a la [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) miembro de función o destruir el `CPen` de objeto para el recurso ya no está en uso. Una aplicación no debe eliminar un lápiz cuando el lápiz está seleccionado en un contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView Nº&100;](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>CPen::CreatePenIndirect  
 Inicializa un lápiz que tiene el estilo, ancho y color proporcionado en la estructura que señala `lpLogPen`.  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpLogPen`  
 Apunta a Windows [LOGPEN](../../mfc/reference/logpen-structure.md) estructura que contiene información sobre el lápiz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Lápices con un ancho superior a 1 píxel siempre debe tener ya sea la **PS_NULL**, **PS_SOLID**, o **PS_INSIDEFRAME** estilo.  
  
 Si tiene un lápiz la **PS_INSIDEFRAME** estilo y un color que no coincide con un color en la tabla de colores lógica, se dibuja el lápiz con un color interpolado. El **PS_INSIDEFRAME** estilo es idéntico a **PS_SOLID** si el ancho del lápiz es menor o igual que 1.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#101;](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>CPen::FromHandle  
 Devuelve un puntero a un `CPen` objeto, dados un identificador a un objeto pen de GDI de Windows.  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>Parámetros  
 *hPen*  
 `HPEN`identificador de lápiz GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CPen` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay un objeto `CPen` asociado al identificador, se crea y asocia un objeto `CPen` temporal. Este temporal `CPen` objeto es válido sólo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal de todos los objetos se eliminan. En otras palabras, el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#105;](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>CPen::GetExtLogPen  
 Obtiene un **EXTLOGPEN** estructura subyacente.  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLogPen`  
 Apunta a una [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) estructura que contiene información sobre el lápiz.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El **EXTLOGPEN** estructura define el estilo, ancho y atributos de pincel de un lápiz. Por ejemplo, llamar a `GetExtLogPen` para que coincida con el estilo determinada de un lápiz.  
  
 Vea los temas siguientes en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener información acerca de los atributos de lápiz:  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo llamar al método `GetExtLogPen` para recuperar los atributos de un lápiz y, a continuación, crear un lápiz cosmético, nueva con el mismo color.  
  
 [!code-cpp[NVC_MFCDocView&#102;](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>CPen::GetLogPen  
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
  
 Vea los temas siguientes en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener información acerca de los atributos de lápiz:  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo llamar al método `GetLogPen` para recuperar un carácter de lápiz y, a continuación, crear un lápiz nuevo y sólido con el mismo color.  
  
 [!code-cpp[NVC_MFCDocView&#103;](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>CPen::operator HPEN  
 Obtiene el identificador de Windows GDI adjunto de la `CPen` objeto.  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto de GDI de Windows representado por la `CPen` objeto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Este operador es un operador de conversión, que admite el uso directo de una `HPEN` objeto.  
  
 Para obtener más información acerca del uso de objetos gráficos, vea el artículo [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#104;](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CBrush (clase)](../../mfc/reference/cbrush-class.md)

