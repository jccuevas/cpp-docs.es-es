---
title: CBrush (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
dev_langs: C++
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c6c567c720f5dc1febe0626754721c7c6ec9af4a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicializa un pincel con el modelo sombreado especificado y el color.|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicializa un pincel con un patrón especificado por un mapa de bits.|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicializa un pincel con el color sólido especificado.|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Crea un pincel que es el color predeterminado del sistema.|  
|[CBrush::FromHandle](#fromhandle)|Devuelve un puntero a un `CBrush` objeto cuando se especifica un identificador a una ventana de `HBRUSH` objeto.|  
|[CBrush::GetLogBrush](#getlogbrush)|Obtiene un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](#operator_hbrush)|Devuelve el identificador de Windows asociado a la `CBrush` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un `CBrush` objeto, construya un `CBrush` objeto y pasarlo a cualquier `CDC` función miembro que requiere un pincel.  
  
 Pinceles pueden ser sólidas, sombreada o entramado.  
  
 Para obtener más información sobre `CBrush`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cbrush"></a>CBrush::CBrush  
 Construye un objeto `CBrush`.  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el color de primer plano del pincel como un color RGB. Si el pincel está sombreado, este parámetro especifica el color de la trama.  
  
 `nIndex`  
 Especifica el estilo de trama del pincel. Puede ser cualquiera de los siguientes valores:  
  
- `HS_BDIAGONAL`Sombreado descendente (de izquierda a derecha) en 45 grados  
  
- `HS_CROSS`Sombreado horizontal y vertical  
  
- `HS_DIAGCROSS`Sombreado doble de 45 grados  
  
- `HS_FDIAGONAL`Sombreado ascendente (de izquierda a derecha) en 45 grados  
  
- `HS_HORIZONTAL`Sombreado horizontal  
  
- `HS_VERTICAL`Sombreado vertical  
  
 `pBitmap`  
 Apunta a un `CBitmap` objeto que especifica un mapa de bits con el que pinta el pincel.  
  
### <a name="remarks"></a>Comentarios  
 `CBrush`tiene cuatro sobrecargados constructores. El constructor sin argumentos crea una sin inicializar `CBrush` objeto que debe inicializarse antes de poder utilizarlo.  
  
 Si utiliza el constructor sin argumentos, debe inicializar resultante `CBrush` objeto con [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), o [CreateDIBPatternBrush](#createdibpatternbrush). Si utiliza uno de los constructores que toma argumentos, a continuación, ninguna otra inicialización es necesaria. Los constructores con argumentos pueden producir una excepción si se encuentran errores, mientras que el constructor sin argumentos siempre se realizará correctamente.  
  
 El constructor con un único [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro construye un pincel sólido con el color especificado. El color se especifica un valor RGB y se pueden construir con el `RGB` macro en WINDOWS. H.  
  
 El constructor con dos parámetros, crea un pincel de trama. El `nIndex` parámetro especifica el índice de un modelo de sombreado. El `crColor` parámetro especifica el color.  
  
 El constructor con un `CBitmap` parámetro construye un pincel de trama. El parámetro identifica un mapa de bits. El mapa de bits se supone que ha creado con [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), o [ CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). El tamaño mínimo para un mapa de bits que se usará en una trama de relleno es 8 x 8 píxeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="createbrushindirect"></a>CBrush::CreateBrushIndirect  
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
 El pincel posteriormente puede seleccionarse como el pincel actual para cualquier contexto de dispositivo.  
  
 Un pincel que se creó mediante un mapa de bits monocromo (1 plano, 1 bit por píxel) se dibuja utilizando los colores de texto y fondo actuales. Con el color de texto actual se dibujará píxeles representados por un bit establecido en 0. Con el color de fondo actual se dibujará píxeles representados por un bit establecido en 1.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush  
 Inicializa un pincel con el patrón especificado por un mapa de bits independiente del dispositivo (DIB).  
  
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
 Especifica si el **[] bmiColors** campos de la [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) estructura de datos (una parte de la "DIB empaquetan") contienen explícita los valores RGB o índices en la paleta lógica actualmente producida. El parámetro debe ser uno de los valores siguientes:  
  
- **DIB_PAL_COLORS** la tabla de colores se compone de una matriz de índices de 16 bits.  
  
- **DIB_RGB_COLORS** la tabla de colores contiene los valores RGB literales.  
  
 *lpPackedDIB*  
 Apunta a un DIB empaquetado que consta de un `BITMAPINFO` estructura seguido inmediatamente por una matriz de bytes que definir los píxeles del mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El pincel posteriormente puede seleccionarse para cualquier contexto de dispositivo que admita operaciones de trama.  
  
 Las dos versiones son distintas en la forma de que controlar el DIB:  
  
-   En la primera versión, para obtener un identificador del archivo DIB se llama a las ventanas **GlobalAlloc** función para asignar un bloque de memoria global y, a continuación, rellenar la memoria con el empaquetado DIB.  
  
-   En la segunda versión, no es necesario llamar a **GlobalAlloc** asignar memoria para el empaquetado DIB.  
  
 DIB empaquetado consta de un `BITMAPINFO` seguido inmediatamente de la matriz de bytes que define los píxeles del mapa de bits de estructura de datos. Mapas de bits que se usa como patrones de relleno deben ser 8 x 8 píxeles. Si el mapa de bits es mayor, Windows crea una trama de relleno con solo los bits correspondientes a las 8 primeras filas y 8 columnas de píxeles en la esquina superior izquierda del mapa de bits.  
  
 Cuando una aplicación, selecciona un pincel de modelo DIB dos colores en un contexto de dispositivo monocromático, Windows pasa por alto los colores especificados en el archivo DIB y en su lugar, muestra el pincel de modelo utilizando los colores de texto y fondo actuales del contexto del dispositivo. Asignada al primer color (con un desplazamiento 0 en la tabla de colores DIB) de la imagen DIB de píxeles se muestran con el color del texto. Píxeles que se asigna al segundo color (en desplazamiento 1 en la tabla de color) se muestran con el color de fondo.  
  
 Para obtener información sobre el uso de las siguientes funciones de Windows, consulte el SDK de Windows:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (esta función se proporciona únicamente por compatibilidad con aplicaciones escritas para versiones de Windows anteriores a la 3.0; utilice la **CreateDIBPatternBrushPt** función.)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) (esta función debe usarse para las aplicaciones basadas en Win32).  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="createhatchbrush"></a>CBrush::CreateHatchBrush  
 Inicializa un pincel con el modelo sombreado especificado y el color.  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el estilo de trama del pincel. Puede ser cualquiera de los siguientes valores:  
  
- `HS_BDIAGONAL`Sombreado descendente (de izquierda a derecha) en 45 grados  
  
- `HS_CROSS`Sombreado horizontal y vertical  
  
- `HS_DIAGCROSS`Sombreado doble de 45 grados  
  
- `HS_FDIAGONAL`Sombreado ascendente (de izquierda a derecha) en 45 grados  
  
- `HS_HORIZONTAL`Sombreado horizontal  
  
- `HS_VERTICAL`Sombreado vertical  
  
 `crColor`  
 Especifica el color de primer plano del pincel como un color RGB (el color de las escotillas). Vea [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) en el SDK de Windows para obtener más información.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El pincel posteriormente puede seleccionarse como el pincel actual para cualquier contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="createpatternbrush"></a>CBrush::CreatePatternBrush  
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
 El pincel posteriormente puede seleccionarse para cualquier contexto de dispositivo que admita operaciones de trama. El mapa de bits identificado por `pBitmap` normalmente se inicializa mediante el [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), o [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) (función).  
  
 Mapas de bits que se usa como patrones de relleno deben ser 8 x 8 píxeles. Si el mapa de bits es mayor, Windows sólo utilizará los bits correspondientes a las 8 primeras filas y columnas de píxeles en la esquina superior izquierda del mapa de bits.  
  
 Un pincel de modelo se puede eliminar sin que ello afecte el mapa de bits asociado. Esto significa que el mapa de bits puede usarse para crear un número arbitrario de pinceles de trama.  
  
 Un pincel que se creó mediante un mapa de bits monocromático (plano 1 color, 1 bit por píxel) se dibuja utilizando los colores de texto y fondo actuales. Píxeles representados por un bit establecido en 0 se dibujan con el color de texto actual. Píxeles representados por un bit establecido en 1 se dibujan con el color de fondo actual.  
  
 Para obtener información sobre el uso de [CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508), una ventana de función, vea el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="createsolidbrush"></a>CBrush::CreateSolidBrush  
 Inicializa un pincel con un color sólido especificado.  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) estructura que especifica el color del pincel. El color se especifica un valor RGB y se pueden construir con el `RGB` macro en WINDOWS. H.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El pincel posteriormente puede seleccionarse como el pincel actual para cualquier contexto de dispositivo.  
  
 Cuando una aplicación ha terminado de usar el pincel creado por `CreateSolidBrush`, debe seleccionar el pincel fuera del contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CBrush::CBrush](#cbrush).  
  
##  <a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush  
 Inicializa un color de pincel.  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica un índice de color. Este valor corresponde al color usado para pintar uno de los elementos de 21 ventana. Vea [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) en el SDK de Windows para obtener una lista de valores.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El pincel posteriormente puede seleccionarse como el pincel actual para cualquier contexto de dispositivo.  
  
 Cuando una aplicación ha terminado de usar el pincel creado por `CreateSysColorBrush`, debe seleccionar el pincel fuera del contexto de dispositivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="fromhandle"></a>CBrush::FromHandle  
 Devuelve un puntero a un `CBrush` objeto cuando se especifica un identificador a una ventana de [HBRUSH](#operator_hbrush) objeto.  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBrush`  
 `HANDLE`en un pincel de GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CBrush` objeto si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CBrush` objeto ya no está asociado al identificador, un archivo temporal `CBrush` se crea y asocia el objeto. Este temporal `CBrush` objeto es válido solo hasta la próxima vez que la aplicación no tiene tiempo de inactividad en el bucle de eventos. En este momento, se eliminan todos los objetos temporales de gráficos. En otras palabras, el objeto temporal es válido solo durante el procesamiento de mensajes de una ventana.  
  
 Para obtener más información sobre el uso de objetos gráficos, consulte [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CBrush::CBrush](#cbrush).  
  
##  <a name="getlogbrush"></a>CBrush::GetLogBrush  
 Llame a esta función miembro para recuperar el `LOGBRUSH` estructura.  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLogBrush`  
 Apunta a un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) estructura que contiene información sobre el pincel.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, y `pLogBrush` es un puntero válido, el valor devuelto es el número de bytes almacenados en el búfer.  
  
 Si la función se realiza correctamente, y `pLogBrush` es **NULL**, el valor devuelto es el número de bytes necesarios para almacenar la información de la función podría almacenar en el búfer.  
  
 Si se produce un error en la función, el valor devuelto es 0.  
  
### <a name="remarks"></a>Comentarios  
 El `LOGBRUSH` estructura define el estilo, el color y el patrón de un pincel.  
  
 Por ejemplo, llamar a `GetLogBrush` para que coincida con el patrón de un mapa de bits o un color determinado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="operator_hbrush"></a>CBrush::operator HBRUSH  
 Utilice este operador para obtener el identificador de GDI de Windows asociado de la `CBrush` objeto.  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto GDI de Windows representado por la `CBrush` objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Éste es un operador de conversión, que admite el uso directo de un `HBRUSH` objeto.  
  
 Para obtener más información sobre el uso de objetos gráficos, consulte [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC PROPDLG](../../visual-cpp-samples.md)   
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CBitmap (clase)](../../mfc/reference/cbitmap-class.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)
