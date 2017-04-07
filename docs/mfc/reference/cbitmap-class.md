---
title: CBitmap (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- drawing, tools
- CBitmap class
- GDI bitmap
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: 22
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
ms.openlocfilehash: ccfe592bbbae8c0eff22baa6e1baac56754ef6fc
ms.lasthandoff: 02/24/2017

---
# <a name="cbitmap-class"></a>CBitmap (clase)
Encapsula un mapa de bits de la Interfaz de dispositivo gráfico (GDI) de Windows y proporciona funciones miembro para manipular el mapa de bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|Construye un objeto `CBitmap`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|Inicializa el objeto con un mapa de bits dependiente del dispositivo de memoria que tiene un ancho especificado, el alto y el patrón de bits.|  
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicializa el objeto con un mapa de bits con el ancho, el alto y el patrón de bits (si se especifica alguna) en un **BITMAP** estructura.|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializa el objeto con un mapa de bits para que sea compatible con un determinado dispositivo.|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializa el objeto con un mapa de bits descartable que sea compatible con un determinado dispositivo.|  
|[CBitmap::FromHandle](#fromhandle)|Devuelve un puntero a un `CBitmap` objeto cuando se especifica un identificador a un Windows `HBITMAP` mapa de bits.|  
|[CBitmap::GetBitmap](#getbitmap)|Rellena un **BITMAP** estructura con información sobre el mapa de bits.|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copia los bits del mapa de bits especificado en el búfer especificado.|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Devuelve el ancho y alto del mapa de bits. El alto y ancho se supone que se ha establecido previamente el [SetBitmapDimension](#setbitmapdimension) función miembro.|  
|[CBitmap:: LoadBitmap](#loadbitmap)|Inicializa el objeto, cargar un recurso de mapa de bits con nombre de archivo ejecutable de la aplicación y asociar el mapa de bits para el objeto.|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Carga un mapa de bits y asigna colores a colores del sistema actual.|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicializa el objeto, cargar un mapa de bits de Windows predefinida y asociar el mapa de bits para el objeto.|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|Establece los bits del mapa de bits a los valores de bits especificado.|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Asigna un ancho y alto a un mapa de bits en unidades de 0,1 milímetros.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de Windows asociado a la `CBitmap` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un `CBitmap` de objeto, construya el objeto, asociar un identificador de mapa de bits con una de las funciones miembro de inicialización y, a continuación, llamar a los miembros del objeto de funciones.  
  
 Para obtener más información sobre el uso de objetos gráficos como `CBitmap`, consulte [gráfico de objetos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cbitmap"></a>CBitmap::CBitmap  
 Construye un objeto `CBitmap`.  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto resultante debe inicializarse con una de las funciones de miembro de la inicialización.  
  
##  <a name="createbitmap"></a>CBitmap::CreateBitmap  
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
  
 Aunque un mapa de bits no se pueden seleccionar directamente para un dispositivo de presentación, puede seleccionarse como el mapa de bits actual un "contexto de dispositivo de memoria" mediante el uso de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) y copiará cualquier contexto de dispositivo compatible con la [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) (función).  
  
 Cuando termine con el objeto `CBitmap` creado por la función `CreateBitmap` , seleccione primero el mapa de bits fuera del contexto del dispositivo y elimine luego el objeto `CBitmap` .  
  
 Para más información, vea la descripción del campo **bmBits** en la estructura **BITMAP** . El [BITMAP](../../mfc/reference/bitmap-structure.md) estructura se describe en el [CBitmap::CreateBitmapIndirect](#createbitmapindirect) función miembro.  
  
##  <a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect  
 Inicializa un mapa de bits que tenga el ancho, el alto y el patrón de bits (si se ha especificado) en la estructura que señala `lpBitmap`.  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBitmap`  
 Apunta a un [BITMAP](../../mfc/reference/bitmap-structure.md) estructura que contiene información sobre el mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Aunque un mapa de bits no se pueden seleccionar directamente para un dispositivo de presentación, puede seleccionarse como el mapa de bits actual para un contexto de dispositivo de memoria mediante el uso de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) y copiará cualquier contexto de dispositivo compatible con la [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) o [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) (función). (El [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) función puede copiar el mapa de bits para el pincel actual directamente en el contexto de dispositivo de pantalla.)  
  
 Si el **mapa de bits** estructura que apunta el `lpBitmap` se ha rellenado parámetro utilizando el `GetObject` función, no se especifican los bits del mapa de bits y el mapa de bits se ha inicializado. Para inicializar el mapa de bits, una aplicación puede utilizar una función como [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) o [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) para copiar los bits del mapa de bits identificado por el primer parámetro de `CGdiObject::GetObject` al mapa de bits creado por `CreateBitmapIndirect`.  
  
 Cuando termine con el `CBitmap` objeto creado con `CreateBitmapIndirect` funcione, primero seleccione el mapa de bits fuera del contexto de dispositivo y luego eliminar el `CBitmap` objeto.  
  
##  <a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap  
 Inicializa un mapa de bits es compatible con el dispositivo especificado por `pDC`.  
  
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
 El mapa de bits tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Se puede seleccionar como el mapa de bits actual para cualquier dispositivo de memoria que es compatible con la especificada por `pDC`.  
  
 Si `pDC` es un contexto de dispositivo de memoria, el mapa de bits devuelto tiene el mismo formato que el mapa de bits actualmente seleccionada en ese contexto de dispositivo. Un "contexto de dispositivo de memoria" es un bloque de memoria que representa una superficie de pantalla. Puede usar para preparar las imágenes en la memoria antes de copiarlos en la superficie de presentación del dispositivo compatible.  
  
 Cuando se crea un contexto de dispositivo de memoria, GDI selecciona automáticamente un mapa de bits monocromo stock para él.  
  
 Puesto que puede tener un contexto de dispositivo de memoria de color color o mapas de bits monocromático seleccionada, el formato del mapa de bits devuelto por la `CreateCompatibleBitmap` función no es siempre el mismo; sin embargo, el formato de un mapa de bits compatible para un contexto de dispositivo no son de memoria siempre está en el formato del dispositivo.  
  
 Cuando termine con el `CBitmap` objeto creado con el `CreateCompatibleBitmap` funcione, primero seleccione el mapa de bits fuera del contexto de dispositivo y luego eliminar el `CBitmap` objeto.  
  
##  <a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap  
 Inicializa un mapa de bits descartable que sea compatible con el contexto de dispositivo identificado por `pDC`.  
  
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
 El mapa de bits tiene el mismo número de planos de color o el mismo formato de bits por píxel que el contexto de dispositivo especificado. Una aplicación puede seleccionar este mapa de bits como el mapa de bits actual para un dispositivo de memoria que es compatible con la especificada por `pDC`.  
  
 Windows puede descartar un mapa de bits creado por esta función sólo si la aplicación no ha seleccionado en un contexto de presentación. Si Windows descarta el mapa de bits cuando no está seleccionada esta opción y posteriormente la aplicación intenta seleccionar, el [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) función devolverá **NULL**.  
  
 Cuando termine con el `CBitmap` objeto creado con el `CreateDiscardableBitmap` funcione, primero seleccione el mapa de bits fuera del contexto de dispositivo y luego eliminar el `CBitmap` objeto.  
  
##  <a name="fromhandle"></a>CBitmap::FromHandle  
 Devuelve un puntero a un `CBitmap` objeto cuando se especifica un identificador de un mapa de bits de GDI de Windows.  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBitmap`  
 Especifica un mapa de bits de GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CBitmap` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CBitmap` objeto no está asociado al identificador de un objeto temporal `CBitmap` objeto creado y conectado. Este temporal `CBitmap` objeto es válido sólo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal de todos los objetos se eliminan. Otra forma de decir esto es que el objeto temporal sólo es válido durante el procesamiento de mensajes de una ventana.  
  
##  <a name="getbitmap"></a>CBitmap::GetBitmap  
 Recupera las propiedades de la imagen del mapa de bits adjunto.  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitMap`  
 Puntero a un [estructura de mapa de bits](../../mfc/reference/bitmap-structure.md) estructura que recibirá las propiedades de la imagen. Este parámetro no debe ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getbitmapbits"></a>CBitmap::GetBitmapBits  
 Copia el patrón de bits del mapa de bits adjunta en el búfer especificado.  
  
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
 El número de bytes copiados en el búfer si el método se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [CBitmap::GetBitmap](#getbitmap) para determinar el tamaño de búfer necesario.  
  
##  <a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension  
 Devuelve el ancho y alto del mapa de bits.  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho y alto del mapa de bits, se miden en unidades de 0,1 milímetros. El alto es en el **cy** miembro de la `CSize` es objeto y el ancho de la **cx** miembro. Si no se ha establecido mediante el mapa de bits ancho y alto `SetBitmapDimension`, el valor devuelto es 0.  
  
### <a name="remarks"></a>Comentarios  
 El alto y ancho se supone que se ha establecido previamente mediante el uso de la [SetBitmapDimension](#setbitmapdimension) función miembro.  
  
##  <a name="loadbitmap"></a>CBitmap:: LoadBitmap  
 Carga el recurso de mapa de bits denominado `lpszResourceName` o identificada por el número de identificación en `nIDResource` desde el archivo ejecutable de la aplicación.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszResourceName`  
 Apunta a una cadena terminada en null que contiene el nombre del recurso de mapa de bits.  
  
 `nIDResource`  
 Especifica el número de identificador de recurso del recurso de mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits cargada se adjunta a la `CBitmap` objeto.  
  
 Si el mapa de bits identificado por `lpszResourceName` no existe o si no hay memoria suficiente para cargar el mapa de bits, la función devuelve 0.  
  
 Puede usar el [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) función para eliminar el mapa de bits cargado por el `LoadBitmap` (función), o la `CBitmap` destructor eliminará el objeto que.  
  
> [!CAUTION]
>  Antes de eliminar el objeto, asegúrese de que no está seleccionada en un contexto de dispositivo.  
  
 Los mapas de bits siguientes se agregaron a las versiones 3.1 y versiones posteriores de Windows:  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 Estos mapas de bits no se encuentran en los controladores de dispositivo para versiones de Windows 3.0 y versiones anteriores. Para obtener una lista completa de los mapas de bits y una presentación de su aspecto, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap  
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
 Un puntero a un **COLORMAP** estructura que contiene la información de color necesaria para asignar los mapas de bits. Si este parámetro es **NULL**, la función utiliza la asignación de colores predeterminada.  
  
 *nMapSize*  
 El número de asignaciones de color señalada por `lpColorMap`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `LoadMappedBitmap` asignará los colores utilizados en los glifos de botón.  
  
 Para obtener información acerca de cómo crear un mapa de bits asignado, vea la función de Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/linkid=230562) y [COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap  
 Carga un mapa de bits predefinido utilizado por Windows.  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDBitmap`  
 Número de Id. de mapa de bits de Windows predefinida. Los valores posibles se muestran debajo de WINDOWS. H:  
  
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
 Mapa de bits de nombres que comienzan por **OBM_OLD** representar mapas de bits utilizados por las versiones de Windows anteriores a la 3.0.  
  
 Tenga en cuenta que la constante **OEMRESOURCE** debe definirse antes de incluir WINDOWS. H para poder utilizar cualquiera de los **OBM_** constantes.  
  
##  <a name="operator_hbitmap"></a>CBitmap::operator HBITMAP  
 Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CBitmap` objeto.  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto de GDI de Windows representado por la `CBitmap` objeto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Este operador es un operador de conversión, que admite el uso directo de una `HBITMAP` objeto.  
  
 Para obtener más información acerca del uso de objetos gráficos, consulte [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setbitmapbits"></a>CBitmap::SetBitmapBits  
 Establece los bits del mapa de bits en los valores de bits especificados por `lpBits`.  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCount`  
 Especifica el número de bytes que apunta `lpBits`.  
  
 `lpBits`  
 Apunta a la **bytes** matriz que contiene los valores de píxel se copien en el `CBitmap` objeto. En orden para el mapa de bits poder representar su imagen correctamente, se deben dar formato de los valores para que se ajuste a los valores de profundidad de alto, ancho y color que se especificaron cuando se creó la instancia CBitmap. Para obtener más información, consulte [CBitmap::CreateBitmap](#createbitmap).  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes utilizados en la configuración de mapa de bits; 0 si se produce un error en la función.  
  
##  <a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension  
 Asigna un ancho y alto a un mapa de bits en unidades de 0,1 milímetros.  
  
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
 Las dimensiones del mapa de bits anterior. Alto es en el **cy** variable miembro de la `CSize` objeto y ancho está en el **cx** variable miembro.  
  
### <a name="remarks"></a>Comentarios  
 La GDI no utiliza estos valores excepto to devolverlos cuando una aplicación llama el [GetBitmapDimension](#getbitmapdimension) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)


