---
title: CFont (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CFont class
- GDI, font classes
- fonts, MFC classes
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cc7ecfb850bf24013acdb55075eeb3d64d4994ee
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cfont-class"></a>CFont (clase)
Encapsula una fuente de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular la fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|Construye un objeto `CFont`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFont:: CreateFont](#createfont)|Inicializa un `CFont` con las características especificadas.|  
|[CFont::CreateFontIndirect](#createfontindirect)|Inicializa un `CFont` objeto con las características de un `LOGFONT` estructura.|  
|[CFont:: CreatePointFont](#createpointfont)|Inicializa un `CFont` con la altura especificada, medida en décimas de un punto y el tipo de letra.|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Igual que `CreateFontIndirect` excepto en que el alto de fuente se mide en décimas de un punto en lugar de unidades lógicas.|  
|[CFont::FromHandle](#fromhandle)|Devuelve un puntero a un `CFont` objeto cuando se especifica un Windows **HFONT**.|  
|[CFont::GetLogFont](#getlogfont)|Rellena un `LOGFONT` con información acerca de la fuente lógica que se adjunta a la `CFont` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFont::operator HFONT](#operator_hfont)|Devuelve el identificador de la fuente de GDI de Windows que se adjunta a la `CFont` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un `CFont` objeto, construir una `CFont` objeto y adjuntar una fuente de Windows con [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), o [CreatePointFontIndirect](#createpointfontindirect)y, a continuación, utilizar funciones de miembro del objeto para manipular la fuente.  
  
 El `CreatePointFont` y `CreatePointFontIndirect` las funciones suelen ser más fáciles de usar que `CreateFont` o `CreateFontIndirect` ya que hacen la conversión para el alto de la fuente de un tamaño de punto de unidades lógicas automáticamente.  
  
 Para obtener más información sobre `CFont`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cfont"></a>CFont::CFont  
 Construye un objeto `CFont`.  
  
```  
CFont();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto resultante se debe inicializar con `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, o `CreatePointFontIndirect` antes de poder usarlo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#70;](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="createfont"></a>CFont:: CreateFont  
 Inicializa un `CFont` objeto con las características especificadas.  
  
```  
BOOL CreateFont(
    int nHeight,  
    int nWidth,  
    int nEscapement,  
    int nOrientation,  
    int nWeight,  
    BYTE bItalic,  
    BYTE bUnderline,  
    BYTE cStrikeOut,  
    BYTE nCharSet,  
    BYTE nOutPrecision,  
    BYTE nClipPrecision,  
    BYTE nQuality,  
    BYTE nPitchAndFamily,  
    LPCTSTR lpszFacename);
```  
  
### <a name="parameters"></a>Parámetros  
 `nHeight`  
 Especifica el alto deseado (en unidades lógicas) de la fuente. Consulte la `lfHeight` miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una descripción. El valor absoluto de `nHeight` no debe superar los 16.384 unidades del dispositivo después de convertirse. Para todas las comparaciones de alto, el asignador de fuentes busca la fuente más grande que no supere el tamaño solicitado o la fuente más pequeña si todas las fuentes superan el tamaño solicitado.  
  
 `nWidth`  
 Especifica el ancho promedio (en unidades lógicas) de caracteres de la fuente. Si `nWidth` es 0, la relación de aspecto del dispositivo se comparará con la relación de aspecto de digitalización de las fuentes disponibles para encontrar la coincidencia más cercana, que viene determinada por el valor absoluto de la diferencia.  
  
 `nEscapement`  
 Especifica el ángulo (en unidades de 0,1 grados) entre el vector de escape y el eje x de la superficie de presentación. El vector de escape es la línea a través de los orígenes de los caracteres primeros y últimos en una línea. El ángulo se mide a la izquierda desde el eje x. Consulte la `lfEscapement` miembro de la `LOGFONT` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información.  
  
 `nOrientation`  
 Especifica el ángulo (en unidades de 0,1 grados) entre la línea de base de un carácter y el eje x. El ángulo se mide a la izquierda desde el eje x para los sistemas de coordenadas en el que la dirección del eje y es hacia abajo y hacia la derecha desde el eje x de los sistemas de coordenadas en el que la dirección del eje está activo.  
  
 `nWeight`  
 Especifica el espesor de fuente (en píxeles dibujados por 1000). Consulte la `lfWeight` miembro de la `LOGFONT` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información. Los valores descritos son aproximados; el aspecto real depende del tipo de letra. Algunas fuentes tienen sólo `FW_NORMAL`, `FW_REGULAR`, y `FW_BOLD` pesos. Si `FW_DONTCARE` se especifica, se utiliza un peso predeterminado.  
  
 `bItalic`  
 Especifica si la fuente está en cursiva.  
  
 `bUnderline`  
 Especifica si la fuente está subrayada.  
  
 `cStrikeOut`  
 Especifica si se tachado caracteres de la fuente. Especifica una fuente de tachado si establece un valor distinto de cero.  
  
 `nCharSet`  
 Especifica setSee de caracteres de la fuente del `lfCharSet` miembro en el `LOGFONT` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de valores.  
  
 El juego de caracteres OEM depende del sistema.  
  
 Las fuentes con otros juegos de caracteres pueden existir en el sistema. Una aplicación que utiliza una fuente con un juego de caracteres desconocido no debe intentar traducir o la interpretación de cadenas que se va a representar con esa fuente. En su lugar, las cadenas deben pasarse directamente al controlador de dispositivo de salida.  
  
 El asignador de fuentes no se utiliza la `DEFAULT_CHARSET` valor. Una aplicación puede utilizar este valor para permitir que el nombre y el tamaño de una fuente para describir completamente la fuente lógica. Si una fuente con el nombre especificado no existe, se puede sustituir una fuente de cualquier conjunto de caracteres de la fuente especificada. Para evitar resultados inesperados, las aplicaciones deben utilizar la `DEFAULT_CHARSET` valor con moderación.  
  
 `nOutPrecision`  
 Especifica la precisión del resultado deseado. La precisión del resultado define el grado de cercanía la salida debe coincidir con la fuente solicitada alto, ancho, orientación de los caracteres, escape y paso. Consulte la `lfOutPrecision` miembro de la `LOGFONT` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de valores y obtener más información.  
  
 `nClipPrecision`  
 Especifica la precisión de recorte deseado. La precisión de recorte define cómo recortar caracteres que están parcialmente fuera de la región de recorte. Consulte la `lfClipPrecision` miembro de la `LOGFONT` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de valores.  
  
 Para utilizar una fuente incrustada de sólo lectura, debe especificar una aplicación `CLIP_ENCAPSULATE`.  
  
 Para lograr la rotación coherente de dispositivo, TrueType y fuentes de vector, una aplicación puede utilizar el operador OR para combinar el `CLIP_LH_ANGLES` valor con cualquiera de los demás `nClipPrecision` valores. Si el `CLIP_LH_ANGLES` bit está establecido, el giro de todas las fuentes depende de si la orientación del sistema de coordenadas es zurda o diestro. (Para obtener más información acerca de la orientación de los sistemas de coordenadas, vea la descripción de la `nOrientation` parámetro.) Si `CLIP_LH_ANGLES` no es, las fuentes de dispositivo siempre Girar a la izquierda, pero la rotación de otras fuentes depende de la orientación del sistema de coordenadas.  
  
 `nQuality`  
 Especifica la calidad de salida de la fuente, que define cómo cuidadosamente la GDI debe intentar hacer coincidir los atributos de fuente lógica con los de una fuente física real. Consulte la `lfQuality` miembro de la `LOGFONT` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de valores.  
  
 `nPitchAndFamily`  
 Especifica el tono y la familia de la fuente. Consulte la `lfPitchAndFamily` miembro de la `LOGFONT` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de valores y obtener más información.  
  
 `lpszFacename`  
 Un `CString` o un puntero a una cadena terminada en null que especifica el nombre de tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. Windows [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619) función puede utilizarse para enumerar todas las fuentes disponibles actualmente. Si `lpszFacename` es `NULL`, la GDI utiliza un tipo de letra independientes del dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar la fuente como la fuente de cualquier contexto de dispositivo.  
  
 El `CreateFont` función no crea una nueva fuente de GDI de Windows. Simplemente se selecciona a la coincidencia más cercana de las fuentes físicas disponibles en el GDI.  
  
 Aplicaciones pueden utilizar la configuración predeterminada para la mayoría de los parámetros cuando se crea una fuente lógica. Los parámetros que siempre se deben proporcionar valores específicos son `nHeight` y `lpszFacename`. Si `nHeight` y `lpszFacename` no se han establecido por la aplicación, la fuente lógica que se crea depende del dispositivo.  
  
 Cuando termine con el `CFont` objeto creado por el `CreateFont` de función, utilice `CDC::SelectObject` para seleccionar una fuente diferente en el contexto de dispositivo, a continuación, elimine la `CFont` objeto que ya no es necesario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#71;](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="createfontindirect"></a>CFont::CreateFontIndirect  
 Inicializa un `CFont` objeto con las características de un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)estructura.  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpLogFont`  
 Apunta a un `LOGFONT` estructura que define las características de la fuente lógica.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar la fuente como la fuente actual para cualquier dispositivo.  
  
 Esta fuente tiene las características especificadas en el [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura. Cuando se selecciona la fuente mediante la [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) función miembro, el asignador de fuentes GDI intenta hacer coincidir la fuente lógica a una fuente física existente. Si se produce un error en el asignador de fuentes buscar a una coincidencia exacta para la fuente lógica, proporciona una fuente alternativa cuyas características coincidan con todas las características solicitadas como sea posible.  
  
 Cuando ya no necesita la `CFont` objeto creado por el `CreateFontIndirect` de función, utilice `CDC::SelectObject` para seleccionar una fuente diferente en el contexto de dispositivo, a continuación, elimine la `CFont` objeto que ya no es necesario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#72;](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="createpointfont"></a>CFont:: CreatePointFont  
 Esta función proporciona una manera sencilla de crear una fuente de un tipo de letra especificada y el tamaño de punto.  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPointSize`  
 Alto de fuente en décimas de un punto solicitado. (Por ejemplo, pasar 120 para solicitar una fuente de 12 puntos).  
  
 `lpszFaceName`  
 Un `CString` o un puntero a una cadena terminada en null que especifica el nombre de tipo de letra de la fuente. La longitud de esta cadena no debe superar los 30 caracteres. Windows **EnumFontFamilies** función puede utilizarse para enumerar todas las fuentes disponibles actualmente. Si `lpszFaceName` es **NULL**, la GDI utiliza un tipo de letra independientes del dispositivo.  
  
 `pDC`  
 Puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto que se va a utilizar para convertir el alto en `nPointSize` de unidades lógicas. Si **NULL**, un contexto de dispositivo de pantalla se utiliza para la conversión.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Convierte automáticamente el alto en `nPointSize` en unidades lógicas utilizando el `CDC` objeto señalado por `pDC`.  
  
 Cuando termine con el `CFont` objeto creado por el `CreatePointFont` funcione, primero seleccione la fuente en el contexto de dispositivo y luego eliminar el `CFont` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#73;](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect  
 Esta función es el mismo que [CreateFontIndirect](#createfontindirect) excepto en que la **lfHeight** miembro de la `LOGFONT` se interpreta en décimas de unidades de un punto en lugar de dispositivo.  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpLogFont`  
 Apunta a un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura que define las características de la fuente lógica. El **lfHeight** miembro de la `LOGFONT` estructura se mide en décimas de un punto en lugar de unidades lógicas. (Por ejemplo, **lfHeight** a 120 para solicitar una fuente de 12 puntos.)  
  
 `pDC`  
 Puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto que se va a utilizar para convertir el alto en **lfHeight** unidades lógicas. Si **NULL**, un contexto de dispositivo de pantalla se utiliza para la conversión.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función convierte automáticamente el alto en **lfHeight** en unidades lógicas utilizando el `CDC` objeto señalado por `pDC` antes de pasar el `LOGFONT` estructura en Windows.  
  
 Cuando termine con el `CFont` objeto creado por el `CreatePointFontIndirect` funcione, primero seleccione la fuente en el contexto de dispositivo y luego eliminar el `CFont` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#74;](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CFont::FromHandle  
 Devuelve un puntero a un `CFont` objeto cuando se especifica un **HFONT** identificador de un objeto de fuente de la GDI de Windows.  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `hFont`  
 Un **HFONT** identificador de una fuente de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CFont` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CFont` objeto no está asociado al identificador de un objeto temporal `CFont` objeto creado y conectado. Este temporal `CFont` objeto es válido sólo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal de todos los objetos se eliminan. Otra forma de decir esto es que el objeto temporal es válido sólo durante el procesamiento de mensajes de una ventana.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#75;](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="getlogfont"></a>CFont::GetLogFont  
 Llame a esta función para recuperar una copia de la `LOGFONT` estructura `CFont`.  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>Parámetros  
 *pLogFont*  
 Puntero a la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura para recibir la información de fuentes.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la función se realiza correctamente, en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#76;](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="operator_hfont"></a>CFont::operator HFONT  
 Utilice este operador para obtener el identificador de GDI de Windows de la fuente que se adjunta a la `CFont` objeto.  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del objeto de fuente de GDI de Windows conectado a `CFont` si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Puesto que este operador se utiliza automáticamente para las conversiones de `CFont` a [fuentes y texto](http://msdn.microsoft.com/library/windows/desktop/dd144819), puede pasar `CFont` objetos a funciones que esperan **HFONT**s.  
  
 Para obtener más información acerca del uso de objetos gráficos, consulte [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#77;](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




