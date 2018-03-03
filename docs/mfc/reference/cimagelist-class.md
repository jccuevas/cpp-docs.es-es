---
title: CImageList (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
dev_langs:
- C++
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1dae44f60c61222659304bea4ee811999d50280b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cimagelist-class"></a>CImageList (clase)
Proporciona la funcionalidad del control de lista de imágenes común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CImageList : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::CImageList](#cimagelist)|Construye un objeto `CImageList`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::Add](#add)|Agrega una imagen o imágenes a una lista de imágenes.|  
|[CImageList::Attach](#attach)|Asocia una lista de imágenes a un `CImageList` objeto.|  
|[CImageList::BeginDrag](#begindrag)|Comienza a arrastrar una imagen.|  
|[CImageList::Copy](#copy)|Copia una imagen dentro de un `CImageList` objeto.|  
|[CImageList:: Create](#create)|Inicializa una lista de imágenes y lo adjunta a un `CImageList` objeto.|  
|[CImageList::DeleteImageList](#deleteimagelist)|Elimina una lista de imágenes.|  
|[CImageList::DeleteTempMap](#deletetempmap)|Llamado por el [CWinApp](../../mfc/reference/cwinapp-class.md) controlador de tiempo de inactividad para eliminar cualquier temporal `CImageList` objeto creado por `FromHandle`.|  
|[CImageList::Detach](#detach)|Desasocia un objeto de lista de imagen desde un `CImageList` de objetos y devuelve un identificador a una lista de imágenes.|  
|[CImageList::DragEnter](#dragenter)|Bloquea las actualizaciones durante una operación de arrastre y muestra la imagen de arrastre en una posición especificada.|  
|[CImageList::DragLeave](#dragleave)|Desbloquea la ventana y oculta la imagen de arrastre para que se puede actualizar la ventana.|  
|[CImageList::DragMove](#dragmove)|Mueve la imagen que se arrastra durante una operación de arrastrar y colocar.|  
|[CImageList::DragShowNolock](#dragshownolock)|Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.|  
|[CImageList::Draw](#draw)|Dibuja la imagen que se arrastra durante una operación de arrastrar y colocar.|  
|[CImageList::DrawEx](#drawex)|Dibuja un elemento de lista de imágenes en el contexto de dispositivo especificado. La función utiliza el estilo de dibujo especificado y combina la imagen con el color especificado.|  
|[CImageList::DrawIndirect](#drawindirect)|Dibuja una imagen de una lista de imágenes.|  
|[CImageList::EndDrag](#enddrag)|Finaliza una operación de arrastre.|  
|[CImageList::ExtractIcon](#extracticon)|Crea un icono en función de una imagen y una máscara en una lista de imágenes.|  
|[CImageList::FromHandle](#fromhandle)|Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador a una lista de imágenes. Si no hay un objeto `CImageList` asociado al identificador, se crea y asocia un objeto `CImageList` temporal.|  
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador a una lista de imágenes. Si un `CImageList` objeto no está asociado al identificador, **NULL** se devuelve.|  
|[CImageList::GetBkColor](#getbkcolor)|Recupera el color de fondo actual para una lista de imágenes.|  
|[CImageList::GetDragImage](#getdragimage)|Obtiene la lista de imágenes temporal que se usa para arrastrar.|  
|[CImageList::GetImageCount](#getimagecount)|Recupera el número de imágenes en una lista de imágenes.|  
|[CImageList::GetImageInfo](#getimageinfo)|Recupera información sobre una imagen.|  
|[CImageList::GetSafeHandle](#getsafehandle)|Recupera **m_hImageList**.|  
|[CImageList::Read](#read)|Lee una lista de imágenes de un archivo.|  
|[CImageList::Remove](#remove)|Quita una imagen de una lista de imágenes.|  
|[CImageList::Replace](#replace)|Reemplaza una imagen en una lista de imágenes con una imagen nueva.|  
|[CImageList::SetBkColor](#setbkcolor)|Establece el color de fondo de una lista de imágenes.|  
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Crea una nueva imagen de arrastre.|  
|[CImageList::SetImageCount](#setimagecount)|Restablece el recuento de las imágenes en una lista de imágenes.|  
|[Función CImageList:: SetOverlayImage](#setoverlayimage)|Agrega el índice de base cero de una imagen a la lista de imágenes que se usará como máscaras superpuestas.|  
|[CImageList::Write](#write)|Escribe una lista de imágenes en un archivo.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Devuelve el `HIMAGELIST` conectado a la `CImageList`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::m_hImageList](#m_himagelist)|Un identificador que contiene la lista de imágenes asociada a este objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Una "lista de imágenes" es una colección de imágenes mismo tamaño, cada uno de los cuales puede hacer referencia por su índice basado en cero. Listas de imágenes se utilizan para administrar eficazmente los grandes conjuntos de iconos o de mapas de bits. Todas las imágenes en una lista de imágenes están contenidas en un mapa de bits única y ancho, en formato de dispositivo de pantalla. Una lista de imágenes también puede incluir un mapa de bits monocromo que contenga máscaras utilizadas para dibujar imágenes de forma transparente (estilo de icono). La aplicación de Microsoft Win32 (API) de la interfaz de programación proporciona funciones de la lista de imágenes que permiten dibujar imágenes, crear y destruir listas de imágenes, agregar y quitar imágenes, reemplazar imágenes, combinar imágenes y arrastrar imágenes.  
  
 Este control (y, por tanto, la `CImageList` clase) está disponible solo para programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Para obtener más información sobre el uso de `CImageList`, consulte [controles](../../mfc/controls-mfc.md) y [utilizar CImageList](../../mfc/using-cimagelist.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="add"></a>CImageList::Add  
 Llame a esta función para agregar una o varias imágenes o en un icono a una lista de imágenes.  
  
```  
int Add(
    CBitmap* pbmImage,  
    CBitmap* pbmMask);

 
int Add(
    CBitmap* pbmImage,  
    COLORREF crMask);  
  
int Add(HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 `pbmImage`  
 Puntero al mapa de bits que contiene la imagen o imágenes. El número de imágenes se deduce el ancho del mapa de bits.  
  
 `pbmMask`  
 Puntero al mapa de bits que contiene la máscara. Si ninguna máscara se utiliza con la lista de imágenes, este parámetro se ignora.  
  
 `crMask`  
 Color utilizado para generar la máscara. Cada píxel de este color del mapa de bits especificado se ha cambiado a negro y el bit correspondiente en la máscara se establece en uno.  
  
 `hIcon`  
 Identificador de un icono que contiene el mapa de bits y una máscara para la nueva imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la primera imagen nueva si es correcto; en caso contrario, - 1.  
  
### <a name="remarks"></a>Comentarios  
 Usted es responsable de liberar el identificador de icono cuando haya terminado con él.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]  
  
##  <a name="attach"></a>CImageList::Attach  
 Llame a esta función para asociar una lista de imágenes a un `CImageList` objeto.  
  
```  
BOOL Attach(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 `hImageList`  
 Un identificador a un objeto de lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el archivo adjunto se realizó correctamente; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]  
  
##  <a name="begindrag"></a>CImageList::BeginDrag  
 Llame a esta función para comenzar a arrastrar una imagen.  
  
```  
BOOL BeginDrag(
    int nImage,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>Parámetros  
 `nImage`  
 Índice de base cero de la imagen de arrastre.  
  
 `ptHotSpot`  
 Coordenadas de la posición inicial de arrastre (normalmente, la posición del cursor). Las coordenadas son con respecto a la esquina superior izquierda de la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función crea una lista de imagen temporal que se usa para arrastrar. La imagen combina la imagen especificada y su máscara con el cursor actual. En respuesta a posteriores `WM_MOUSEMOVE` mensajes, puede mover la imagen de arrastre mediante el `DragMove` función miembro. Para finalizar la operación de arrastre, puede usar el `EndDrag` función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]  
  
##  <a name="cimagelist"></a>CImageList::CImageList  
 Construye un objeto `CImageList`.  
  
```  
CImageList();
```  
  
##  <a name="copy"></a>CImageList::Copy  
 Esta función miembro implementa el comportamiento de la función de Win32 [ImageList_Copy](http://msdn.microsoft.com/library/windows/desktop/bb761520), tal y como se describe en el SDK de Windows.  
  
```  
BOOL Copy(
    int iDst,  
    int iSrc,  
    UINT uFlags = ILCF_MOVE);

 
BOOL Copy(
    int iDst,  
    CImageList* pSrc,  
    int iSrc,  
    UINT uFlags = ILCF_MOVE);
```  
  
### <a name="parameters"></a>Parámetros  
 *iDst*  
 Índice de base cero de la imagen que se usará como el destino de la operación de copia.  
  
 `iSrc`  
 Índice de base cero de la imagen que se usará como el origen de la operación de copia.  
  
 `uFlags`  
 El valor de marca de bits que especifica el tipo de operación de copia se realiza. Este parámetro puede ser uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`ILCF_MOVE`|La imagen de origen se copia en el índice de la imagen de destino. Esta operación genera varias instancias de una imagen determinada. `ILCF_MOVE` es el valor predeterminado.|  
|`ILCF_SWAP`|Las imágenes de origen y destino intercambian posiciones dentro de la lista de imágenes.|  
  
 `pSrc`  
 Un puntero a un `CImageList` objeto que es el destino de la operación de copia.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]  
  
##  <a name="create"></a>CImageList:: Create  
 Inicializa una lista de imágenes y lo adjunta a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.  
  
```  
BOOL Create(
    int cx,  
    int cy,  
    UINT nFlags,  
    int nInitial,  
    int nGrow);

 
BOOL Create(
    UINT nBitmapID,  
    int cx,  
    int nGrow,  
    COLORREF crMask);

 
BOOL Create(
    LPCTSTR lpszBitmapID,  
    int cx,  
    int nGrow,  
    COLORREF crMask);

 
BOOL Create(
    CImageList& imagelist1,  
    int nImage1,  
    CImageList& imagelist2,  
    int nImage2,  
    int dx,  
    int dy);  
  
BOOL Create(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 `cx`  
 Dimensiones de cada imagen, en píxeles.  
  
 `cy`  
 Dimensiones de cada imagen, en píxeles.  
  
 `nFlags`  
 Especifica el tipo de lista de imágenes para crear. Este parámetro puede ser una combinación de los siguientes valores, pero puede incluir solo uno de los `ILC_COLOR` valores.  
  
|Valor|Significado|  
|-----------|-------------|  
|`ILC_COLOR`|Usar el comportamiento predeterminado si no hay ninguno de los demás `ILC_COLOR`* marcas se especificaron. Normalmente, el valor predeterminado es `ILC_COLOR4`; pero para los controladores de pantalla anteriores, el valor predeterminado es `ILC_COLORDDB`.|  
|`ILC_COLOR4`|Usar una sección de mapa de bits independiente del dispositivo (DIB) de 4 bits (16 colores) como el mapa de bits para la lista de imágenes.|  
|`ILC_COLOR8`|Utilice una sección DIB de 8 bits. Los colores usados para la tabla de colores son los mismos colores como la paleta de medios tonos.|  
|`ILC_COLOR16`|Usar 16 bits (32 o 64k color) sección DIB.|  
|`ILC_COLOR24`|Usar una sección DIB de 24 bits.|  
|`ILC_COLOR32`|Usar una sección DIB de 32 bits.|  
|`ILC_COLORDDB`|Utilice un mapa de bits dependiente del dispositivo.|  
|`ILC_MASK`|Utiliza una máscara. La lista de imágenes contiene dos mapas de bits, uno de los cuales es un mapa de bits monocromático utilizado como una máscara. Si este valor no se incluye, la lista de imágenes contiene sólo un mapa de bits. Vea [dibujar imágenes de una lista de imágenes](../../mfc/drawing-images-from-an-image-list.md) para obtener información adicional sobre las imágenes enmascaradas.|  
  
 `nInitial`  
 Número de imágenes que inicialmente contiene la lista de imágenes.  
  
 `nGrow`  
 Número de imágenes que puede alcanzar la lista de imágenes cuando el sistema tiene que cambiar el tamaño de la lista para dejar espacio para nuevas imágenes. Este parámetro representa el número de nuevas imágenes que puede contener la lista de imágenes cuyo tamaño ha cambiado.  
  
 `nBitmapID`  
 Identificadores de recurso del mapa de bits que se asociará con la lista de imágenes.  
  
 `crMask`  
 Color utilizado para generar una máscara. Cada píxel de este color del mapa de bits especificado se ha cambiado a negro y el bit correspondiente en la máscara se establece en uno.  
  
 `lpszBitmapID`  
 Una cadena que contiene los identificadores de las imágenes de recursos.  
  
 `imagelist1`  
 Referencia a un objeto `CImageList`.  
  
 `nImage1`  
 Índice de la primera imagen existente.  
  
 `imagelist2`  
 Referencia a un objeto `CImageList`.  
  
 `nImage2`  
 Índice de la segunda imagen existente.  
  
 `dx`  
 Desplazamiento del eje x de la segunda imagen en relación con la primera imagen, en píxeles.  
  
 `dy`  
 Desplazamiento del eje y de la segunda imagen en relación con la primera imagen, en píxeles.  
  
 `pImageList`  
 Un puntero a un `CImageList` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CImageList` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea la lista de imágenes y lo adjunta a la `CImageList` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]  
  
##  <a name="deleteimagelist"></a>CImageList::DeleteImageList  
 Llame a esta función para eliminar una lista de imágenes.  
  
```  
BOOL DeleteImageList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]  
  
##  <a name="deletetempmap"></a>CImageList::DeleteTempMap  
 Llama de forma automática la `CWinApp` controlador de tiempo de inactividad, `DeleteTempMap` elimina cualquier temporal `CImageList` objetos creados por [FromHandle](#fromhandle), pero no destruirá los identificadores ( `hImageList`) temporalmente asociados con el **ImageList** objetos.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]  
  
##  <a name="detach"></a>CImageList::Detach  
 Llame a esta función para desconectar un objeto de lista de imagen desde un `CImageList` objeto.  
  
```  
HIMAGELIST Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador a un objeto de lista de imágenes.  
  
### <a name="remarks"></a>Comentarios  
 Esta función devuelve un identificador para el objeto de lista de imágenes.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CImageList::Attach](#attach).  
  
##  <a name="dragenter"></a>CImageList::DragEnter  
 Durante una operación de arrastre, bloquea las actualizaciones de la ventana especificada por `pWndLock` y muestra la imagen de arrastre en la posición especificada por `point`.  
  
```  
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndLock`  
 Puntero a la ventana que posee la imagen de arrastre.  
  
 `point`  
 Posición en la que se va a mostrar la imagen de arrastre. Coordenadas son relativas a la esquina superior izquierda de la ventana (no en el área de cliente).  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Las coordenadas son con respecto a esquina superior izquierda la ventana en la, por lo que debe compensar los anchos de los elementos de ventana, como el borde, la barra de título y la barra de menús, al especificar las coordenadas.  
  
 Si `pWndLock` es **NULL**, esta función dibuja la imagen en el contexto de presentación asociado a la ventana del escritorio y coordenadas son relativas a la esquina superior izquierda de la pantalla.  
  
 Esta función bloquea todas las demás actualizaciones a la ventana especificada durante la operación de arrastre. Si necesita realizar un dibujo durante una operación de arrastre, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada utilizando la [CImageList::DragLeave](#dragleave) (función).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CImageList::BeginDrag](#begindrag).  
  
##  <a name="dragleave"></a>CImageList::DragLeave  
 Desbloquea la ventana especificada por `pWndLock` y oculta la imagen de arrastre, lo que permite la ventana para actualizarse.  
  
```  
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndLock`  
 Puntero a la ventana que posee la imagen de arrastre.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CImageList::EndDrag](#enddrag).  
  
##  <a name="dragmove"></a>CImageList::DragMove  
 Llame a esta función para mover la imagen que se arrastra durante una operación de arrastrar y colocar.  
  
```  
static BOOL PASCAL DragMove(CPoint pt);
```  
  
### <a name="parameters"></a>Parámetros  
 `pt`  
 Nueva posición de arrastre.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se denomina normalmente en respuesta a un `WM_MOUSEMOVE` mensaje. Para comenzar una operación de arrastre, use la `BeginDrag` función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]  
  
##  <a name="dragshownolock"></a>CImageList::DragShowNolock  
 Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.  
  
```  
static BOOL PASCAL DragShowNolock(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 `bShow`  
 Especifica si se mostrará la imagen de arrastre.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El [CImageList::DragEnter](#dragenter) función bloquea todas las actualizaciones de la ventana durante una operación de arrastre. Sin embargo, esta función no bloquea la ventana.  
  
##  <a name="draw"></a>CImageList::Draw  
 Llame a esta función para dibujar la imagen que se arrastra durante una operación de arrastrar y colocar.  
  
```  
BOOL Draw(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de dispositivo de destino.  
  
 `nImage`  
 Índice de base cero de la imagen para dibujar.  
  
 `pt`  
 Ubicación en la que se va a dibujar dentro del contexto de dispositivo especificado.  
  
 `nStyle`  
 Indicador que especifica el estilo de dibujo. Puede ser uno o varios de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`ILD_BLEND25`, **ILD_FOCUS**|Dibuja la imagen, mezcla 25 por ciento con el color de resaltado del sistema. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|  
|`ILD_BLEND50`, **ILD_SELECTED**, **ILD_BLEND**|Dibuja la imagen, mezcla 50 por ciento con el color de resaltado del sistema. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|  
|**ILD_MASK**|Dibuja la máscara.|  
|`ILD_NORMAL`|Dibuja la imagen con el color de fondo de la lista de imágenes. Si el color de fondo es la `CLR_NONE` valor, la imagen se dibuja de forma transparente mediante la máscara.|  
|`ILD_TRANSPARENT`|Dibuja la imagen de forma transparente mediante la máscara, sin tener en cuenta el color de fondo.|  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [función CImageList:: SetOverlayImage](#setoverlayimage).  
  
##  <a name="drawex"></a>CImageList::DrawEx  
 Dibuja un elemento de lista de imágenes en el contexto de dispositivo especificado.  
  
```  
BOOL DrawEx(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    SIZE sz,  
    COLORREF clrBk,  
    COLORREF clrFg,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de dispositivo de destino.  
  
 `nImage`  
 Índice de base cero de la imagen para dibujar.  
  
 `pt`  
 Ubicación en la que se va a dibujar dentro del contexto de dispositivo especificado.  
  
 `sz`  
 Tamaño de la parte de la imagen para dibujar con respecto a la esquina superior izquierda de la imagen. Vea `dx` y *dy* en [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) en el SDK de Windows.  
  
 *clrBk*  
 Color de fondo de la imagen. Vea *rgbBk* en [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) en el SDK de Windows.  
  
 *clrFg*  
 Color de primer plano de la imagen. Vea *rgbFg* en [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) en el SDK de Windows.  
  
 `nStyle`  
 Indicador que especifica el estilo de dibujo. Vea *fStyle* en [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La función utiliza el estilo de dibujo especificado y combina la imagen con el color especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]  
  
##  <a name="drawindirect"></a>CImageList::DrawIndirect  
 Llame a esta función miembro para dibujar una imagen de una lista de imágenes.  
  
```  
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

 
BOOL DrawIndirect(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    SIZE sz,  
    POINT ptOrigin,  
    UINT fStyle = ILD_NORMAL,  
    DWORD dwRop = SRCCOPY,  
    COLORREF rgbBack = CLR_DEFAULT,  
    COLORREF rgbFore = CLR_DEFAULT,  
    DWORD fState = ILS_NORMAL,  
    DWORD Frame = 0,  
    COLORREF crEffect = CLR_DEFAULT);
```  
  
### <a name="parameters"></a>Parámetros  
 *pimldp*  
 Un puntero a un [estructura IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) estructura que contiene información sobre la operación de dibujo.  
  
 `pDC`  
 Un puntero al contexto de dispositivo de destino. Debe eliminar este [CDC](../../mfc/reference/cdc-class.md) objeto cuando haya terminado con él.  
  
 `nImage`  
 Índice de base cero de la imagen para dibujar.  
  
 `pt`  
 A [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura que contiene las coordenadas x e y donde se dibujará la imagen.  
  
 `sz`  
 A [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que indica el tamaño de la imagen para dibujar.  
  
 *ptOrigin*  
 A [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura que contiene las coordenadas x e y especificar la esquina superior izquierda de la operación de dibujo con respecto a la propia imagen. No se dibujan los píxeles de la imagen que están a la izquierda de la coordenada x y versiones posteriores de la coordenada y.  
  
 `fStyle`  
 Indicador que especifica el estilo de dibujo y, opcionalmente, la imagen de superposición. Vea la sección Comentarios para obtener información sobre la imagen de superposición. La implementación predeterminada MFC, `ILD_NORMAL`, dibuja la imagen con el color de fondo de la lista de imágenes. Si el color de fondo es la `CLR_NONE` valor, la imagen se dibuja de forma transparente con una máscara.  
  
 Otros estilos posibles se describen en la **fStyle** miembro de la [estructura IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) estructura.  
  
 *dwRop*  
 Valor que especifica un código de operación de trama. Estos códigos definen cómo se combinan los datos de color para el rectángulo de origen con los datos de color para el rectángulo de destino lograr el color final. Implementación, de predeterminada de MFC **SRCCOPY**, copia el rectángulo de origen directamente en el rectángulo de destino. Este parámetro se omite si el `fStyle` parámetro no incluye el **ILD_ROP** marca.  
  
 Otros valores posibles se describen en la **dwRop** miembro de la [estructura IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) estructura.  
  
 *rgbBack*  
 El color de fondo de imagen, de forma predeterminada `CLR_DEFAULT`. Este parámetro puede ser un valor definido por la aplicación de RGB o uno de los valores siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|`CLR_DEFAULT`|Color de fondo predeterminado. La imagen se dibuja utilizando el color de fondo de la lista de imágenes.|  
|`CLR_NONE`|Ningún color de fondo. La imagen se dibuja de forma transparente.|  
  
 *rgbFore*  
 Color de primer plano, la imagen predeterminada `CLR_DEFAULT`. Este parámetro puede ser un valor definido por la aplicación de RGB o uno de los valores siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|`CLR_DEFAULT`|Color de primer plano predeterminado. La imagen se dibuja utilizando el color de resaltado del sistema como el color de primer plano.|  
|`CLR_NONE`|Ningún color de blend. La imagen se mezcla con el color del contexto de dispositivo de destino.|  
  
 Este parámetro se utiliza sólo si `fStyle` incluye la `ILD_BLEND25` o `ILD_BLEND50` marca.  
  
 *fState*  
 Indicador que especifica el estado de dibujo. Este miembro puede contener uno o más indicadores de estado de lista de imágenes.  
  
 *Frame*  
 Afecta al comportamiento de efectos saturados y combinación alfa.  
  
 Cuando se usa con **ILS_SATURATE**, este miembro contiene el valor que se agrega a cada componente de la terna RGB para cada píxel en el icono de color.  
  
 Cuando se usa con **ILS_APLHA**, este miembro contiene el valor para el canal alfa. Este valor puede estar entre 0 y 255, donde 0 es completamente transparente y 255 es completamente opaco.  
  
 *crEffect*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor utilizado para los efectos de resplandor e instantáneas.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la imagen es dibujado correctamente; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Si desea rellenar la estructura de Win32 usted mismo, utilice la primera versión. Use la segunda versión si desea sacar partido de uno o varios de los argumentos predeterminados de MFC, o si se evita la administración de la estructura.  
  
 Una imagen de superposición es una imagen que se dibuja encima de la imagen principal, especificada en esta función miembro por el `nImage` parámetro. Dibujar una máscara superpuesta con el [dibujar](#draw) función miembro con el índice basado en uno de la máscara de superposición especificada mediante el uso de la [macro INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) macro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]  
  
##  <a name="enddrag"></a>CImageList::EndDrag  
 Llame a esta función para finalizar una operación de arrastre.  
  
```  
static void PASCAL EndDrag();
```  
  
### <a name="remarks"></a>Comentarios  
 Para comenzar una operación de arrastre, use la `BeginDrag` función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]  
  
##  <a name="extracticon"></a>CImageList::ExtractIcon  
 Llame a esta función para crear un icono que se basa en una imagen y su máscara relacionado en una lista de imágenes.  
  
```  
HICON ExtractIcon(int nImage);
```  
  
### <a name="parameters"></a>Parámetros  
 `nImage`  
 Índice de base cero de la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del icono si se realiza correctamente; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Este método se basa en el comportamiento de la [ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401) macro para crear el icono. Hacer referencia a la [ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401) macro para obtener más información sobre la creación de icono y limpieza.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]  
  
##  <a name="fromhandle"></a>CImageList::FromHandle  
 Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador a una lista de imágenes.  
  
```  
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 `hImageList`  
 Especifica la lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CImageList` objeto si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CImageList` ya no está asociado al identificador, un archivo temporal `CImageList` se crea y asocia el objeto. Este temporal `CImageList` objeto es válido solo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, en qué momento se eliminan todos los objetos temporales.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]  
  
##  <a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent  
 Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador a una lista de imágenes.  
  
```  
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 `hImageList`  
 Especifica la lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CImageList` objeto si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CImageList` objeto no está asociado al identificador, **NULL** se devuelve.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]  
  
##  <a name="getbkcolor"></a>CImageList::GetBkColor  
 Llame a esta función para recuperar el color de fondo actual para una lista de imágenes.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de color RGB de la `CImageList` color de fondo del objeto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CImageList::SetBkColor](#setbkcolor).  
  
##  <a name="getdragimage"></a>CImageList::GetDragImage  
 Obtiene la lista de imágenes temporal que se usa para arrastrar.  
  
```  
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,  
    LPPOINT lpPointHotSpot);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoint`  
 Dirección de un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura que recibe la actual posición de arrastre.  
  
 *lpPointHotSpot*  
 Dirección de un **punto** estructura que recibe el desplazamiento de la imagen de arrastre con respecto a la posición de arrastre.  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un puntero a la imagen temporal una lista que se utiliza para operaciones de arrastre; en caso contrario, **NULL**.  
  
##  <a name="getimagecount"></a>CImageList::GetImageCount  
 Llame a esta función para recuperar el número de imágenes en una lista de imágenes.  
  
```  
int GetImageCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de imágenes.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CImageList::ExtractIcon](#extracticon).  
  
##  <a name="getimageinfo"></a>CImageList::GetImageInfo  
 Llame a esta función para recuperar información sobre una imagen.  
  
```  
BOOL GetImageInfo(
    int nImage,  
    IMAGEINFO* pImageInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nImage`  
 Índice de base cero de la imagen.  
  
 *pImageInfo*  
 Puntero a un [IMAGEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761393) estructura que recibe información sobre la imagen. La información de esta estructura puede utilizarse para manipular directamente los mapas de bits de la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El `IMAGEINFO` estructura contiene información sobre una imagen en una lista de imágenes.  
  
##  <a name="getsafehandle"></a>CImageList::GetSafeHandle  
 Llame a esta función para recuperar el **m_hImageList** miembro de datos.  
  
```  
HIMAGELIST GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de la lista de imágenes asociadas; en caso contrario, **NULL** si no está conectado a ningún objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]  
  
##  <a name="m_himagelist"></a>CImageList::m_hImageList  
 Identificador de la lista de imágenes asociado a este objeto.  
  
 **HIMAGELIST m_hImageList;**  
  
### <a name="remarks"></a>Comentarios  
 El **m_hImageList** miembro de datos es una variable pública de tipo `HIMAGELIST`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]  
  
##  <a name="operator_himagelist"></a>CImageList::operator HIMAGELIST  
 Utilice este operador para obtener el identificador de adjunta el `CImageList` objeto.  
  
```  
operator HIMAGELIST() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador de la lista de imágenes representado por la `CImageList` objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Éste es un operador de conversión, que admite el uso directo de un `HIMAGELIST` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]  
  
##  <a name="read"></a>CImageList::Read  
 Llame a esta función para leer una lista de imágenes de un archivo.  
  
```  
BOOL Read(CArchive* pArchive);
```  
  
### <a name="parameters"></a>Parámetros  
 `pArchive`  
 Un puntero a un `CArchive` objeto desde el que se puede leer la lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]  
  
##  <a name="remove"></a>CImageList::Remove  
 Llame a esta función para quitar una imagen de un objeto de lista de imágenes.  
  
```  
BOOL Remove(int nImage);
```  
  
### <a name="parameters"></a>Parámetros  
 `nImage`  
 Índice de base cero de la imagen para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Todos los elementos que siguen a `nImage` ahora Bajar una posición. Por ejemplo, si una lista de imágenes contiene dos elementos, eliminar el primer elemento hará que el resto de producto esté ahora en la primera posición. `nImage`= 0 para el elemento en la primera posición.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]  
  
##  <a name="replace"></a>CImageList::Replace  
 Llame a esta función para reemplazar una imagen en una lista de imágenes con una imagen nueva.  
  
```  
BOOL Replace(
    int nImage,  
    CBitmap* pbmImage,  
    CBitmap* pbmMask);

 
int Replace(
    int nImage,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 `nImage`  
 Índice de base cero de la imagen para reemplazar.  
  
 `pbmImage`  
 Un puntero al mapa de bits que contiene la imagen.  
  
 `pbmMask`  
 Un puntero al mapa de bits que contiene la máscara. Si ninguna máscara se utiliza con la lista de imágenes, este parámetro se ignora.  
  
 `hIcon`  
 Identificador del icono que contiene el mapa de bits y una máscara para la nueva imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 La versión devolver **BOOL** devuelve es distinto de cero si es correcto; en caso contrario, 0.  
  
 La versión devolver `int` devuelve el índice de base cero de la imagen si es correcto; en caso contrario - 1.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro después de llamar a [función SetImageCount](#setimagecount) para asignar el nuevo, las imágenes válidas para el marcador de posición de la imagen números de índice.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CImageList::SetImageCount](#setimagecount).  
  
##  <a name="setbkcolor"></a>CImageList::SetBkColor  
 Llame a esta función para establecer el color de fondo de una lista de imágenes.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parámetros  
 `cr`  
 Color de fondo a establecer. Puede ser `CLR_NONE`. En ese caso, imágenes se dibujan de forma transparente mediante la máscara.  
  
### <a name="return-value"></a>Valor devuelto  
 El color de fondo anterior si se realiza correctamente; en caso contrario, `CLR_NONE`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]  
  
##  <a name="setdragcursorimage"></a>CImageList::SetDragCursorImage  
 Crea una nueva imagen de arrastre combinando la imagen dada (normalmente una imagen del cursor del mouse) con la imagen de arrastre actual.  
  
```  
BOOL SetDragCursorImage(
    int nDrag,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>Parámetros  
 *nDrag*  
 Índice de la nueva imagen que se combinarán con la imagen de arrastre.  
  
 `ptHotSpot`  
 Posición de la zona activa en la nueva imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Dado que las funciones de arrastre utilizan la nueva imagen durante una operación de arrastre, debe utilizar las ventanas [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396) función para ocultar el cursor del mouse actual después de llamar a `CImageList::SetDragCursorImage`. En caso contrario, puede parecer que el sistema tiene dos cursores del mouse para la duración de la operación de arrastre.  
  
##  <a name="setimagecount"></a>CImageList::SetImageCount  
 Llame a esta función miembro para restablecer el número de imágenes en un `CImageList` objeto.  
  
```  
BOOL SetImageCount(UINT uNewCount);
```  
  
### <a name="parameters"></a>Parámetros  
 *uNewCount*  
 El valor que se especifica el nuevo número total de imágenes en la lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si se llama a esta función miembro para aumentar el número de imágenes en la lista de imágenes, a continuación, llame a [reemplazar](#replace) para cada imagen adicional asignar los nuevos índices a las imágenes válidas. Si no puede asignar los índices a las imágenes válidas, las operaciones de dibujo que crean las imágenes nuevas serán impredecibles.  
  
 Si reduce el tamaño de una lista de imágenes mediante el uso de esta función, se liberan las imágenes truncadas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]  
  
##  <a name="setoverlayimage"></a>Función CImageList:: SetOverlayImage  
 Llame a esta función para agregar el índice de base cero de una imagen a la lista de imágenes que se usará como máscaras superpuestas.  
  
```  
BOOL SetOverlayImage(
    int nImage,  
    int nOverlay);
```  
  
### <a name="parameters"></a>Parámetros  
 `nImage`  
 Índice de base cero de la imagen que se usará como una máscara superpuesta.  
  
 *nOverlay*  
 Índice basado en uno de la máscara de superposición.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Hasta cuatro índices pueden agregarse a la lista.  
  
 Una máscara superpuesta es una imagen dibujada de forma transparente sobre otra imagen. Dibuja una máscara superpuesta sobre una imagen mediante el uso de la [CImageList::Draw](#draw) función miembro con el índice basado en uno de la máscara de superposición especificada mediante el uso de la **macro INDEXTOOVERLAYMASK** macro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]  
  
##  <a name="write"></a>CImageList::Write  
 Llame a esta función para escribir un objeto de lista de imágenes en un archivo.  
  
```  
BOOL Write(CArchive* pArchive);
```  
  
### <a name="parameters"></a>Parámetros  
 `pArchive`  
 Un puntero a un `CArchive` objeto en el que se almacenará la lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)
