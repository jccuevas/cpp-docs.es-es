---
title: CAnimateCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
dev_langs:
- C++
helpviewer_keywords:
- animation controls [C++], CAnimateCtrl class
- Windows common controls [C++], CAnimateCtrl class
- CAnimateCtrl class
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
caps.latest.revision: 25
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c4b8472a0dd8d2470f8e069e144efd0949201266
ms.lasthandoff: 04/01/2017

---
# <a name="canimatectrl-class"></a>CAnimateCtrl (clase)
Proporciona la funcionalidad del control común de animación de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimateCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Construye un objeto `CAnimateCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimateCtrl::Close](#close)|Cierra el clip AVI.|  
|[CAnimateCtrl::Create](#create)|Crea un control de animación y lo adjunta a un `CAnimateCtrl` objeto.|  
|[CAnimateCtrl::CreateEx](#createex)|Crea un control de animación con los estilos extendidos de Windows especificados y lo adjunta a un `CAnimateCtrl` objeto.|  
|[CAnimateCtrl::IsPlaying](#isplaying)|Indica si se trata de un clip de Audio y vídeo intercalado (AVI).|  
|[CAnimateCtrl::Open](#open)|Abre un clip AVI desde un archivo o recurso y muestra el primer fotograma.|  
|[CAnimateCtrl::Play](#play)|Reproduce el clip AVI sin sonido.|  
|[CAnimateCtrl::Seek](#seek)|Muestra un solo fotograma seleccionado del clip AVI.|  
|[CAnimateCtrl::Stop](#stop)|Detiene la reproducción del clip AVI.|  
  
## <a name="remarks"></a>Comentarios  
 Este control (y, por tanto, la `CAnimateCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95, Windows 98 y Windows NT versión 3.51 y posteriores.  
  
 Un control de animación es una ventana rectangular que muestra un clip en formato AVI (Audio y vídeo intercalado): el formato de audio/vídeo de Windows estándar. Un clip AVI es una serie de marcos de mapa de bits, como una película.  
  
 Controles de animación pueden reproducir solo los clips AVI sencillos. En concreto, los clips para reproducirse en un control de animación deben cumplir los siguientes requisitos:  
  
-   Debe haber exactamente una secuencia de vídeo y debe tener al menos un fotograma.  
  
-   Puede haber a lo sumo dos flujos en el archivo (normalmente la otra secuencia, si está presente, es una secuencia de audio, aunque el control de animación omite la información de audio).  
  
-   El clip debe sin comprimir o se comprimió con compresión RLE8.  
  
-   No hay cambios de la paleta se permiten en la secuencia de vídeo.  
  
 Puede agregar el clip AVI a la aplicación como un recurso AVI o puede acompañar a la aplicación como un archivo AVI independiente.  
  
 Dado que el subproceso continúa ejecutándose mientras se muestra el clip AVI, un uso común de un control de animación es indicar la actividad del sistema durante una operación larga. Por ejemplo, el cuadro de diálogo de búsqueda del explorador de archivos muestra una lupa móvil como el sistema busca un archivo.  
  
 Si crea un `CAnimateCtrl` de objeto dentro de un cuadro de diálogo cuadro, o desde un recurso de cuadro de diálogo con el editor de cuadro de diálogo, se se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un `CAnimateCtrl` de objeto dentro de una ventana, puede que necesite destruirlo. Si crea el `CAnimateCtrl` del objeto en la pila, se destruye automáticamente. Si crea el `CAnimateCtrl` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** del objeto que se va a destruir. Si deriva una clase nueva a partir `CAnimateCtrl` y asigna memoria en esa clase, invalide el `CAnimateCtrl` destructor para deshacerse de las asignaciones.  
  
 Para obtener más información sobre el uso de `CAnimateCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CAnimateCtrl](../../mfc/using-canimatectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl  
 Construye un objeto `CAnimateCtrl`.  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a la [crear](#create) función de miembro para poder realizar ninguna otra operación en el objeto que se crea.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog nº 56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>CAnimateCtrl::Close  
 Cierra el clip AVI que se ha abierto previamente en el control de animación (si existe) y lo quita de la memoria.  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="create"></a>CAnimateCtrl::Create  
 Crea un control de animación y lo adjunta a un `CAnimateCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de animación. Aplicar cualquier combinación de las ventanas de estilos que se describe en la siguiente sección de comentarios y los estilos de control de animación que se describen en [estilos de Control de animación](http://msdn.microsoft.com/library/windows/desktop/bb761886) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `rect`  
 Especifica la posición y el tamaño del control de animación. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
 `pParentWnd`  
 Especifica la animación ventana del control primario, normalmente un `CDialog`. No debe ser **NULL.**  
  
 `nID`  
 Especifica el identificador. del control de animación  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CAnimateCtrl` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de animación y lo adjunta a la `CAnimateCtrl` objeto.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/window-styles.md) a un control de animación.  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
 Si desea utilizar los estilos extendidos de windows con el control de animación, llame a [CreateEx](#createex) en lugar de **crear**.  
  
 Además de los estilos de ventana mencionados anteriormente, puede que desee aplicar uno o varios de los estilos de control de animación a un control de animación. Consulte la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre [estilos de control de animación](http://msdn.microsoft.com/library/windows/desktop/bb761886).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="createex"></a>CAnimateCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CAnimateCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Especifica el estilo del control de animación. Aplicar cualquier combinación de la ventana y estilos de control de animación que se describen en [estilos de Control de animación](http://msdn.microsoft.com/library/windows/desktop/bb761886) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente de `pParentWnd`.  
  
 `pParentWnd`  
 Un puntero a la ventana que es primario del control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="isplaying"></a>CAnimateCtrl::IsPlaying  
 Indica si se trata de un clip de Audio y vídeo intercalado (AVI).  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si se trata de un clip AVI; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [ACM_ISPLAYING](http://msdn.microsoft.com/library/windows/desktop/bb761895) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="open"></a>CAnimateCtrl::Open  
 Llame a esta función para abrir un clip AVI y mostrar su primer fotograma.  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFileName`  
 Un `CString` objeto o un puntero a una cadena terminada en null que contiene el nombre del archivo AVI o el nombre de un recurso AVI. Si este parámetro es **NULL**, el sistema cierra el clip AVI que se ha abierto previamente para el control de animación, si lo hay.  
  
 `nID`  
 El identificador de recursos AVI. Si este parámetro es **NULL**, el sistema cierra el clip AVI que se ha abierto previamente para el control de animación, si lo hay.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El recurso AVI se carga desde el módulo que creó el control de animación.  
  
 **Abra** no admite el sonido de un clip AVI; puede abrir únicamente los clips AVI silenciosos.  
  
 Si el control de animación tiene la `ACS_AUTOPLAY` estilo, el control de animación automáticamente empezará a reproducirse el clip inmediatamente después de que éste abre. Seguirá reproducir el clip en segundo plano mientras el subproceso continúa la ejecución. Cuando haya terminado el clip de reproducción en curso, automáticamente se repetirá.  
  
 Si el control de animación tiene la `ACS_CENTER` estilo, el clip AVI se centrará en el control y no se cambiará el tamaño del control. Si el control de animación no tiene el `ACS_CENTER` estilo, el control se ajustará cuando se abre el clip AVI en el tamaño de las imágenes en el clip AVI. La posición de la esquina superior izquierda del control no cambiará, solo el tamaño del control.  
  
 Si el control de animación tiene la `ACS_TRANSPARENT` estilo, el primer fotograma se dibuja utilizando un fondo transparente en lugar de especifica el color de fondo en el clip de animación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="play"></a>CAnimateCtrl::Play  
 Llame a esta función para reproducir un clip AVI en un control de animación.  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>Parámetros  
 `nFrom`  
 Índice de base cero del marco de la que comienza la reproducción en curso. Valor debe ser inferior a 65.536. Un valor de 0 significa que comienzan por el primer fotograma en el clip AVI.  
  
 `nTo`  
 Índice de base cero del marco de reproducción donde finaliza. Valor debe ser inferior a 65.536. Un valor de - 1 significa terminar con el último fotograma en el clip AVI.  
  
 *nRep*  
 Número de veces que se reproducirá el clip AVI. Un valor de - 1 indica que se vuelve a reproducir el archivo indefinidamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El control de animación reproducirá el clip en segundo plano mientras el subproceso continúa la ejecución. Si el control de animación tiene `ACS_TRANSPARENT` estilo, el clip AVI se reproducirá con un fondo transparente en lugar de con el color de fondo especificado en el clip de animación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="seek"></a>CAnimateCtrl::Seek  
 Llame a esta función para mostrar estáticamente un solo fotograma del clip AVI.  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>Parámetros  
 `nTo`  
 Índice de base cero del marco para mostrar. Valor debe ser inferior a 65.536. Un valor de 0 significa que muestre el primer fotograma en el clip AVI. Un valor de -1 significa mostrando el último fotograma en el clip AVI.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si el control de animación tiene `ACS_TRANSPARENT` estilo, se dibujará el clip AVI con un fondo transparente en lugar de especifica el color de fondo en el clip de animación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="stop"></a>CAnimateCtrl::Stop  
 Llame a esta función para detener la reproducción de un clip AVI en un control de animación.  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL](message-map-macros-mfc.md#on_control)


