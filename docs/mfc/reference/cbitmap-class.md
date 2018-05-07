---
title: CBitmap (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs:
- C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5b931c7ad4b560ce247f78dcb126f9669bceb67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cbitmap-class"></a>CBitmap (clase)
Encapsula un mapa de bits de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular el mapa de bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|Construye un objeto `CBitmap`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|Inicializa el objeto con un mapa de bits de memoria dependiente de dispositivo que tiene un ancho especificado, el alto y el patrón de bits.|  
|[CBitmap:: Createbitmapindirect](#createbitmapindirect)|Inicializa el objeto con un mapa de bits con el ancho, el alto y el patrón de bits (si se especifica alguna) proporcionado una **mapa de bits** estructura.|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializa el objeto con un mapa de bits para que sea compatible con un determinado dispositivo.|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializa el objeto con un mapa de bits no descartable que sea compatible con un determinado dispositivo.|  
|[CBitmap::FromHandle](#fromhandle)|Devuelve un puntero a un `CBitmap` objeto cuando se especifica un identificador a una ventana `HBITMAP` mapa de bits.|  
|[CBitmap::GetBitmap](#getbitmap)|Rellena un **mapa de bits** estructura con información sobre el mapa de bits.|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copia los bits del mapa de bits especificado en el búfer especificado.|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Devuelve el ancho y alto del mapa de bits. El alto y ancho se supone que se ha establecido previamente el [SetBitmapDimension](#setbitmapdimension) función miembro.|  
|[CBitmap:: LoadBitmap](#loadbitmap)|Inicializa el objeto si carga un recurso de mapa de bits con nombre de archivo ejecutable de la aplicación y se asocia el mapa de bits para el objeto.|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Carga un mapa de bits y mapas de colores para los colores del sistema actual.|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicializa el objeto si carga un mapa de bits de Windows predefinida y se asocia el mapa de bits para el objeto.|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|Establece los bits de un mapa de bits en los valores de bits especificado.|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Asigna un ancho y alto de un mapa de bits en unidades de 0,1 milímetros.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de Windows asociado a la `CBitmap` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un `CBitmap` objeto, construya el objeto, asocie un identificador de mapa de bits a ella con una de las funciones de miembro de inicialización y, a continuación, llamar a los miembros del objeto de funciones.  
  
 Para obtener más información sobre el uso de objetos gráficos como `CBitmap`, consulte [gráfico de objetos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cbitmap"></a>  CBitmap::CBitmap  
 Construye un objeto `CBitmap`.  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto resultante debe inicializarse con una de las funciones de miembro de inicialización.  
  
##  <a name="createbitmap"></a>  CBitmap::CreateBitmap  
 Inicializa un mapa de bits de memoria dependiente de dispositivo que tiene el ancho, el alto y el patrón de bits especificados.  
  
```  
BOOL CreateBitmap(
    int nWidth,  
    int nHeight,  
    UINT nPlanes,  
    UINT nBitcount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 Especifica el ancho (en píxeles) del mapa de bits.  
  
 `nHeight`  
 Especifica el alto (en píxeles) del mapa de bits.  
  
 `nPlanes`  
 Especifica el número de planos de color del mapa de bits.  
  
 `nBitcount`  
 Especifica el número de bits de color por píxel de la pantalla.  
  
 `lpBits`  
 Apunta a una matriz de bytes que contiene los valores de bits de mapa de bits iniciales. Si es **NULL**, el nuevo mapa de bits se deja sin inicializar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para un mapa de bits de color, el parámetro `nPlanes` o `nBitcount` debe establecerse en 1. Si ambos parámetros se establecen en 1, `CreateBitmap` crea un mapa de bits monocromo.  
  
 Aunque un mapa de bits no se puede seleccionar directamente para un dispositivo de pantalla, puede seleccionarse como el mapa de bits actual para un "contexto de dispositivo de memoria" usando [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) y se copian en cualquier contexto de dispositivo compatibles mediante el uso de la [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) función.  
  
 Cuando termine con el objeto `CBitmap` creado por la función `CreateBitmap` , seleccione primero el mapa de bits fuera del contexto del dispositivo y elimine luego el objeto `CBitmap` .  
  
 Para más información, vea la descripción del campo **bmBits** en la estructura **BITMAP** . El [mapa de bits](../../mfc/reference/bitmap-structure.md) estructura se describe en el [CBitmap:: Createbitmapindirect](#createbitmapindirect) función miembro.  
  
##  <a name="createbitmapindirect"></a>  CBitmap:: Createbitmapindirect  
 Inicializa un mapa de bits que tenga el ancho, el alto y el patrón de bits (si se especifica alguna) proporcionado en la estructura que señala `lpBitmap`.  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBitmap`  
 Apunta a un [mapa de bits](../../mfc/reference/bitmap-structure.md) estructura que contiene información sobre el mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Aunque un mapa de bits no se puede seleccionar directamente para un dispositivo de pantalla, puede seleccionarse como el mapa de bits actual para un contexto de dispositivo de memoria mediante el uso de [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) y se copian en cualquier contexto de dispositivo compatibles mediante el uso de la [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) o [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) (función). (El [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) función puede copiar el mapa de bits para el pincel actual directamente en el contexto de dispositivo de pantalla.)  
  
 Si el **mapa de bits** estructura que señala el `lpBitmap` ha sido rellenado parámetro mediante el uso de la `GetObject` función, no se especifican los bits del mapa de bits y el mapa de bits no está inicializado. Para inicializar el mapa de bits, una aplicación puede usar una función como [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) o [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) para copiar los bits del mapa de bits identificado por el primer parámetro de `CGdiObject::GetObject` al mapa de bits creado por `CreateBitmapIndirect`.  
  
 Cuando termine con el `CBitmap` objeto creado con `CreateBitmapIndirect` funcione, primero seleccione el mapa de bits fuera del contexto de dispositivo y luego elimine la `CBitmap` objeto.  
  
##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap  
 Inicializa un mapa de bits que es compatible con el dispositivo especificado por `pDC`.  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Especifica el contexto de dispositivo.  
  
 `nWidth`  
 Especifica el ancho (en píxeles) del mapa de bits.  
  
 `nHeight`  
 Especifica el alto (en píxeles) del mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits no tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Solo puede seleccionarse como el mapa de bits actual para cualquier dispositivo de memoria que es compatible con la especificada por `pDC`.  
  
 Si `pDC` es un contexto de dispositivo de memoria, el mapa de bits devuelto tiene el mismo formato que el mapa de bits actualmente seleccionada en ese contexto de dispositivo. Un "contexto de dispositivo de memoria" es un bloque de memoria que representa una superficie de presentación. Se puede utilizar para preparar las imágenes en la memoria antes de copiarlos en la superficie de pantalla real del dispositivo compatible.  
  
 Cuando se crea un contexto de dispositivo de memoria, GDI selecciona automáticamente un mapa de bits monocromático cotizaciones para él.  
  
 Ya que puede tener un contexto de dispositivo de memoria de color color o mapas de bits monocromático seleccionada, el formato del mapa de bits devuelto por la `CreateCompatibleBitmap` función no es siempre la misma; sin embargo, el formato de un mapa de bits compatible para un contexto de dispositivo no son de memoria siempre está en el formato del dispositivo.  
  
 Cuando termine con el `CBitmap` objeto creado con la `CreateCompatibleBitmap` funcione, primero seleccione el mapa de bits fuera del contexto de dispositivo y luego elimine la `CBitmap` objeto.  
  
##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap  
 Inicializa un mapa de bits no descartable que sea compatible con el contexto de dispositivo identificado por `pDC`.  
  
```  
BOOL CreateDiscardableBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Especifica un contexto de dispositivo.  
  
 `nWidth`  
 Especifica el ancho (en bits) del mapa de bits.  
  
 `nHeight`  
 Especifica el alto (en bits) del mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits no tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Una aplicación puede seleccionar este mapa de bits como el mapa de bits actual para un dispositivo de memoria que es compatible con la especificada por `pDC`.  
  
 Windows puede descartar un mapa de bits creado por esta función solo si una aplicación no lo ha seleccionado en un contexto de presentación. Si Windows descarta el mapa de bits cuando no está seleccionada y la aplicación más tarde intenta seleccionarlo, el [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) función devolverá **NULL**.  
  
 Cuando termine con el `CBitmap` objeto creado con la `CreateDiscardableBitmap` funcione, primero seleccione el mapa de bits fuera del contexto de dispositivo y luego elimine la `CBitmap` objeto.  
  
##  <a name="fromhandle"></a>  CBitmap::FromHandle  
 Devuelve un puntero a un `CBitmap` objeto cuando se especifica un identificador a un mapa de bits de GDI de Windows.  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBitmap`  
 Especifica un mapa de bits de GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CBitmap` objeto si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CBitmap` objeto ya no está asociado al identificador, un archivo temporal `CBitmap` se crea y asocia el objeto. Este temporal `CBitmap` objeto es válido solo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal todos los objetos se eliminan. Otra manera de decir esto es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
##  <a name="getbitmap"></a>  CBitmap::GetBitmap  
 Recupera las propiedades de imagen para el mapa de bits adjunto.  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitMap`  
 Puntero a un [estructura de mapa de bits](../../mfc/reference/bitmap-structure.md) estructura que va a recibir las propiedades de la imagen. Este parámetro no debe ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits  
 Copia el patrón de bits del mapa de bits que se adjunta en el búfer especificado.  
  
```  
DWORD GetBitmapBits(
    DWORD dwCount,  
    LPVOID lpBits) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCount`  
 El número de bytes que se deben copiar en el búfer.  
  
 `lpBits`  
 Puntero al búfer que recibirá el mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes copiados en el búfer si el método se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Use [CBitmap::GetBitmap](#getbitmap) para determinar el tamaño de búfer necesario.  
  
##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension  
 Devuelve el ancho y alto del mapa de bits.  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho y alto del mapa de bits, se mide en unidades de 0,1 milímetros. El alto es en el **cy** miembro de la `CSize` objeto y el ancho se encuentra en la **cx** miembro. Si el ancho del mapa de bits y el alto no se ha establecido mediante el uso de `SetBitmapDimension`, el valor devuelto es 0.  
  
### <a name="remarks"></a>Comentarios  
 El alto y ancho se supone que se ha establecido previamente mediante el uso de la [SetBitmapDimension](#setbitmapdimension) función miembro.  
  
##  <a name="loadbitmap"></a>  CBitmap:: LoadBitmap  
 Carga el recurso del mapa de bits denominado por `lpszResourceName` o identificada por el número de identificación en `nIDResource` del archivo ejecutable de la aplicación.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszResourceName`  
 Apunta a una cadena terminada en null que contiene el nombre del recurso de mapa de bits.  
  
 `nIDResource`  
 Especifica el número de Id. de recurso del recurso de mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits cargado se adjunta a la `CBitmap` objeto.  
  
 Si el mapa de bits identificado por `lpszResourceName` no existe o si no hay memoria suficiente para cargar el mapa de bits, la función devuelve 0.  
  
 Puede usar el [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función para eliminar el mapa de bits cargado por el `LoadBitmap` función, o la `CBitmap` destructor eliminará el objeto para usted.  
  
> [!CAUTION]
>  Antes de eliminar el objeto, asegúrese de que no está seleccionada en un contexto de dispositivo.  
  
 Los mapas de bits siguientes se agregaron a versiones de Windows 3.1 y posteriores:  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 Estos mapas de bits no se encuentran en los controladores de dispositivo para versiones de Windows 3.0 y versiones anteriores. Para obtener una lista completa de los mapas de bits y una presentación de su aspecto, consulte el SDK de Windows.  
  
##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap  
 Llame a esta función miembro para cargar un mapa de bits y los colores se asignan a los colores del sistema actual.  
  
```  
BOOL LoadMappedBitmap(
    UINT nIDBitmap,  
    UINT nFlags = 0,  
    LPCOLORMAP lpColorMap = NULL,  
    int nMapSize = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDBitmap`  
 El identificador del recurso de mapa de bits.  
  
 `nFlags`  
 Una marca para un mapa de bits. Puede ser cero o **CMB_MASKED**.  
  
 `lpColorMap`  
 Un puntero a un **COLORMAP** estructura que contiene la información de color necesaria para asignar los mapas de bits. Si este parámetro es **NULL**, la función utiliza el mapa de colores predeterminada.  
  
 *nMapSize*  
 El número de mapas de colores que señala `lpColorMap`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `LoadMappedBitmap` asignará colores que se usan habitualmente en los glifos de botón.  
  
 Para obtener información acerca de cómo crear un mapa de bits asignado, vea la función de Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562) y [COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448) estructura en el SDK de Windows.  
  
##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap  
 Carga un mapa de bits predefinida utilizada por Windows.  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDBitmap`  
 Número de identificación del mapa de bits de Windows predefinida. Los valores posibles se muestran a continuación de WINDOWS. H:  
  
|||  
|-|-|  
|**OBM_BTNCORNERS**|**OBM_OLD_RESTORE**|  
|**OBM_BTSIZE**|**OBM_OLD_RGARROW**|  
|**OBM_CHECK**|**OBM_OLD_UPARROW**|  
|**OBM_CHECKBOXES**|**OBM_OLD_ZOOM**|  
|**OBM_CLOSE**|**OBM_REDUCE**|  
|**OBM_COMBO**|**OBM_REDUCED**|  
|**OBM_DNARROW**|**OBM_RESTORE**|  
|**OBM_DNARROWD**|**OBM_RESTORED**|  
|**OBM_DNARROWI**|**OBM_RGARROW**|  
|**OBM_LFARROW**|**OBM_RGARROWD**|  
|**OBM_LFARROWD**|**OBM_RGARROWI**|  
|**OBM_LFARROWI**|**OBM_SIZE**|  
|**OBM_MNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_CLOSE**|**OBM_UPARROWD**|  
|**OBM_OLD_DNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_LFARROW**|**OBM_ZOOM**|  
|**OBM_OLD_REDUCE**|**OBM_ZOOMD**|  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Mapa de bits de nombres que comienzan por **OBM_OLD** representan los mapas de bits que se usaba en las versiones de Windows anteriores a 3.0.  
  
 Tenga en cuenta que la constante **OEMRESOURCE** debe definirse antes de incluir WINDOWS. H para poder utilizar cualquiera de los **OBM_** constantes.  
  
##  <a name="operator_hbitmap"></a>  CBitmap::operator HBITMAP  
 Utilice este operador para obtener el identificador de GDI de Windows asociado de la `CBitmap` objeto.  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto GDI de Windows representado por la `CBitmap` objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Éste es un operador de conversión, que admite el uso directo de un `HBITMAP` objeto.  
  
 Para obtener más información sobre el uso de objetos gráficos, consulte [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el SDK de Windows.  
  
##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits  
 Establece los bits de un mapa de bits en los valores de bit proporcionados por `lpBits`.  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCount`  
 Especifica el número de bytes que señala `lpBits`.  
  
 `lpBits`  
 Apunta a la **bytes** matriz que contiene los valores de píxel que se copiará en la `CBitmap` objeto. En orden del mapa de bits poder representar su imagen correctamente, se deben dar formato de los valores para que se ajuste a los valores de profundidad de alto, ancho y color que se especificaron cuando se creó la instancia CBitmap. Para obtener más información, consulte [CBitmap::CreateBitmap](#createbitmap).  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes utilizados en la configuración de los bits de mapa de bits; 0 si se produce un error en la función.  
  
##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension  
 Asigna un ancho y alto de un mapa de bits en unidades de 0,1 milímetros.  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 Especifica el ancho del mapa de bits (en unidades de 0,1 milímetros).  
  
 `nHeight`  
 Especifica el alto del mapa de bits (en unidades de 0,1 milímetros).  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones del mapa de bits anterior. Alto está en el **cy** variable miembro de la `CSize` objeto y el ancho se encuentra en la **cx** variable miembro.  
  
### <a name="remarks"></a>Comentarios  
 La GDI no usa estos valores excepto to devolverlos cuando una aplicación llama a la [GetBitmapDimension](#getbitmapdimension) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

