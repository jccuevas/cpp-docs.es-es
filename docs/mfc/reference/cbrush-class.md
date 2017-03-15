---
title: CBrush (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBrush
dev_langs:
- C++
helpviewer_keywords:
- brushes, CBrush class
- CBrush class
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
caps.latest.revision: 21
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
ms.openlocfilehash: efcbe2757de3a7e4621e2b20c88726ead111cf8c
ms.lasthandoff: 02/24/2017

---
# <a name="cbrush-class"></a>CBrush (clase)
Encapsula un pincel de la Interfaz de dispositivo gráfico (GDI) de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|Construye un objeto `CBrush`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicializa un pincel con el estilo, el color y el patrón especificado en un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura.|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicializa un pincel con un patrón especificado por un mapa de bits independiente del dispositivo (DIB).|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicializa un pincel con el patrón especificado de sombreado y color.|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicializa un pincel con un patrón especificado por un mapa de bits.|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicializa un pincel de color sólido especificado.|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Crea un pincel de color predeterminado del sistema.|  
|[CBrush::FromHandle](#fromhandle)|Devuelve un puntero a un `CBrush` objeto cuando se especifica un identificador a un Windows `HBRUSH` objeto.|  
|[CBrush::GetLogBrush](#getlogbrush)|Obtiene un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](#operator_hbrush)|Devuelve el identificador de Windows asociado a la `CBrush` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un `CBrush` objeto, construir una `CBrush` objeto y pasarlo a cualquier `CDC` función miembro que requiere un pincel.  
  
 Pinceles pueden ser sólidos, sombreada o entramado.  
  
 Para obtener más información sobre `CBrush`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecbrusha--cbrushcbrush"></a><a name="cbrush"></a>CBrush::CBrush  
 Construye un objeto `CBrush`.  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el color de primer plano del pincel como un color RGB. Si el pincel es sombreado, este parámetro especifica el color de la trama.  
  
 `nIndex`  
 Especifica el estilo de trama del pincel. Puede ser cualquiera de los siguientes valores:  
  
- `HS_BDIAGONAL`Sombreado descendente (de izquierda a derecha) de 45 grados  
  
- `HS_CROSS`Sombreado horizontal y vertical  
  
- `HS_DIAGCROSS`Sombreado doble de 45 grados  
  
- `HS_FDIAGONAL`Sombreado ascendente (de izquierda a derecha) de 45 grados  
  
- `HS_HORIZONTAL`Sombreado horizontal  
  
- `HS_VERTICAL`Sombreado vertical  
  
 `pBitmap`  
 Apunta a un `CBitmap` objeto que especifica un mapa de bits con el que pinta el pincel.  
  
### <a name="remarks"></a>Comentarios  
 `CBrush`tiene cuatro sobrecargados constructores. El constructor sin argumentos crea una variable `CBrush` objeto que se debe inicializar antes de poder usarlo.  
  
 Si utiliza el constructor sin argumentos, debe inicializar resultante `CBrush` objeto con [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), o [CreateDIBPatternBrush](#createdibpatternbrush). Si utiliza uno de los constructores que toma argumentos, a continuación, no es necesaria la inicialización. Los constructores con argumentos pueden producir una excepción si se producen errores, mientras que el constructor sin argumentos siempre se realizará correctamente.  
  
 El constructor con un único [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro construye un pincel sólido con el color especificado. El color se especifica un valor RGB y puede crearse con el `RGB` macro en WINDOWS. H.  
  
 El constructor con dos parámetros, crea un pincel de trama. El `nIndex` parámetro especifica el índice de un modelo de sombreado. El `crColor` parámetro especifica el color.  
  
 El constructor con un `CBitmap` parámetro construye un pincel de trama. El parámetro identifica un mapa de bits. Se supone que el mapa de bits creados mediante [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), o [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). El tamaño mínimo para un mapa de bits que se utilizará en una trama de relleno es 8 x 8 píxeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFCDocView](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="a-namecreatebrushindirecta--cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush::CreateBrushIndirect  
 Inicializa un pincel con un estilo, el color y el patrón especificado en un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura.  
  
```  
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpLogBrush*  
 Apunta a un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura que contiene información sobre el pincel.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.  
  
 Un pincel creado utilizando un mapa de bits monocromo (plano 1, 1 bit por píxel) se dibuja con los colores de fondo y de texto actuales. Píxeles representados por un bit establecido en 0 se dibuja con el color de texto actual. Píxeles representados por un bit establecido en 1 se dibuja con el color de fondo actual.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#22;](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="a-namecreatedibpatternbrusha--cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush  
 Inicializa un pincel con el modelo especificado por un mapa de bits independiente del dispositivo (DIB).  
  
```  
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,  
    UINT nUsage);

 
BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,  
    UINT nUsage);
```  
  
### <a name="parameters"></a>Parámetros  
 *hPackedDIB*  
 Identifica un objeto de memoria global que contiene un mapa de bits empaquetado de independientes del dispositivo (DIB).  
  
 *nUsage*  
 Especifica si la **[] bmiColors** campos de la [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) estructura de datos (parte de "empaquetan DIB") contienen explícita valores RGB o índices en la paleta lógica actualmente realizada. El parámetro debe ser uno de los siguientes valores:  
  
- **DIB_PAL_COLORS** la tabla de colores se compone de una matriz de índices de 16 bits.  
  
- **DIB_RGB_COLORS** la tabla de colores contiene valores RGB literales.  
  
 *lpPackedDIB*  
 Apunta a un DIB empaquetado que consta de un `BITMAPINFO` estructura seguido inmediatamente por una matriz de bytes que definir los píxeles del mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar el pincel para cualquier contexto de dispositivo que admita operaciones paralelas.  
  
 Las dos versiones difieren en la forma de que controlar el formato DIB:  
  
-   En la primera versión, para obtener un identificador del archivo DIB llamar a Windows **GlobalAlloc** función para asignar un bloque de memoria global y, a continuación, rellene la memoria con el formato DIB empaquetado.  
  
-   En la segunda versión, no es necesario llamar a **GlobalAlloc** asignar memoria para el formato DIB empaquetado.  
  
 Empaquetado DIB consta de un `BITMAPINFO` seguido inmediatamente de la matriz de bytes que define los píxeles del mapa de bits de estructura de datos. Mapas de bits que se utiliza como patrones de relleno deben ser de 8 x 8 píxeles. Si el mapa de bits es mayor, Windows crea una trama de relleno usando sólo los bits correspondientes a las 8 primeras filas y 8 columnas píxeles de la esquina superior izquierda del mapa de bits.  
  
 Cuando una aplicación selecciona un pincel de modelo DIB dos colores en un contexto de dispositivo monocromático, Windows pasa por alto los colores especificados en el formato DIB y en su lugar muestra el pincel de modelo utilizando los colores de texto y fondo actuales del contexto de dispositivo. Asignada al primer color (en el desplazamiento 0 en la tabla de colores DIB) de la imagen DIB de píxeles se muestran con el color del texto. Píxeles asignados al segundo color (desplazamiento 1 en la tabla de colores) se muestran con el color de fondo.  
  
 Para obtener información acerca del uso de las siguientes funciones de Windows, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (esta función se proporciona únicamente por compatibilidad con aplicaciones escritas para versiones de Windows anteriores a la 3.0; utilice la **CreateDIBPatternBrushPt** función.)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) (esta función debe usarse para aplicaciones basadas en Win32).  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFCDocView #](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="a-namecreatehatchbrusha--cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush::CreateHatchBrush  
 Inicializa un pincel con el patrón especificado de sombreado y color.  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el estilo de trama del pincel. Puede ser cualquiera de los siguientes valores:  
  
- `HS_BDIAGONAL`Sombreado descendente (de izquierda a derecha) de 45 grados  
  
- `HS_CROSS`Sombreado horizontal y vertical  
  
- `HS_DIAGCROSS`Sombreado doble de 45 grados  
  
- `HS_FDIAGONAL`Sombreado ascendente (de izquierda a derecha) de 45 grados  
  
- `HS_HORIZONTAL`Sombreado horizontal  
  
- `HS_VERTICAL`Sombreado vertical  
  
 `crColor`  
 Especifica el color de primer plano del pincel como un color RGB (el color de los sombreados). Consulte [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#24;](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="a-namecreatepatternbrusha--cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush::CreatePatternBrush  
 Inicializa un pincel con un patrón especificado por un mapa de bits.  
  
```  
BOOL CreatePatternBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitmap`  
 Identifica un mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar el pincel para cualquier contexto de dispositivo que admita operaciones paralelas. El mapa de bits identificado por `pBitmap` normalmente se inicializa mediante el [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), o [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) (función).  
  
 Mapas de bits que se utiliza como patrones de relleno deben ser de 8 x 8 píxeles. Si el mapa de bits es mayor, Windows sólo utilizará los bits correspondientes a las 8 primeras filas y columnas de píxeles en la esquina superior izquierda del mapa de bits.  
  
 Un pincel de modelo puede eliminarse sin afectar el mapa de bits asociado. Esto significa que el mapa de bits puede usarse para crear cualquier número de pinceles de trama.  
  
 Un pincel creado utilizando un mapa de bits monocromático (plano de color de 1, 1 bit por píxel) se dibuja con los colores de fondo y de texto actuales. Píxeles representados por un bit establecido en 0 se dibujan con el color de texto actual. Píxeles representados por un bit establecido en 1 se dibujan con el color de fondo actual.  
  
 Para obtener información sobre el uso de [CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508), una función de Windows, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#25;](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="a-namecreatesolidbrusha--cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush::CreateSolidBrush  
 Inicializa un pincel con un color sólido especificado.  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) estructura que especifica el color del pincel. El color se especifica un valor RGB y puede crearse con el `RGB` macro en WINDOWS. H.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.  
  
 Cuando una aplicación ha terminado con el pincel creado por `CreateSolidBrush`, debe seleccionar el pincel en el contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CBrush::CBrush](#cbrush).  
  
##  <a name="a-namecreatesyscolorbrusha--cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush  
 Inicializa un color de pincel.  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica un índice de color. Este valor corresponde al color usado para dibujar uno de los elementos de la ventana de 21. Consulte [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de valores.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente se puede seleccionar el pincel como pincel actual para cualquier contexto de dispositivo.  
  
 Cuando una aplicación ha terminado con el pincel creado por `CreateSysColorBrush`, debe seleccionar el pincel en el contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFCDocView #](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="a-namefromhandlea--cbrushfromhandle"></a><a name="fromhandle"></a>CBrush::FromHandle  
 Devuelve un puntero a un `CBrush` objeto cuando se especifica un identificador a un Windows [HBRUSH](#operator_hbrush) objeto.  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBrush`  
 `HANDLE`un pincel de GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CBrush` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CBrush` objeto no está asociado al identificador de un objeto temporal `CBrush` objeto creado y conectado. Este temporal `CBrush` objeto es válido sólo hasta la próxima vez que la aplicación tiene el tiempo de inactividad en el bucle de eventos. En este momento, se eliminan todos los objetos de gráficos temporales. En otras palabras, el objeto temporal es válido solo durante el procesamiento de mensajes de una ventana.  
  
 Para obtener más información acerca del uso de objetos gráficos, consulte [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CBrush::CBrush](#cbrush).  
  
##  <a name="a-namegetlogbrusha--cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush::GetLogBrush  
 Llame a esta función miembro para recuperar el `LOGBRUSH` estructura.  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLogBrush`  
 Apunta a un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura que contiene información sobre el pincel.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, y `pLogBrush` es un puntero válido, el valor devuelto es el número de bytes almacenados en el búfer.  
  
 Si la función se realiza correctamente, y `pLogBrush` es **NULL**, el valor devuelto es el número de bytes necesarios para almacenar la información de la función se almacenarían en el búfer.  
  
 Si se produce un error en la función, el valor devuelto es 0.  
  
### <a name="remarks"></a>Comentarios  
 El `LOGBRUSH` estructura define el estilo, el color y el patrón de un pincel.  
  
 Por ejemplo, llamar a `GetLogBrush` para que coincida con el patrón de un mapa de bits o un color determinado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView Nº&27;](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="a-nameoperatorhbrusha--cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush::operator HBRUSH  
 Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CBrush` objeto.  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto de GDI de Windows representado por la `CBrush` objeto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Este operador es un operador de conversión, que admite el uso directo de una `HBRUSH` objeto.  
  
 Para obtener más información acerca del uso de objetos gráficos, consulte [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#28;](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC PROPDLG](../../visual-cpp-samples.md)   
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CBitmap (clase)](../../mfc/reference/cbitmap-class.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)

