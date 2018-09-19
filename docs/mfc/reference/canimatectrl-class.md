---
title: CAnimateCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e921faf20fd7c2bbac967bf73b62dd33c8220a4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688233"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl (clase)
Proporciona la funcionalidad del control común de animación de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimateCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Construye un objeto `CAnimateCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimateCtrl::Close](#close)|Cierra el clip AVI.|  
|[CAnimateCtrl::Create](#create)|Crea un control de animación y lo adjunta a un `CAnimateCtrl` objeto.|  
|[CAnimateCtrl::CreateEx](#createex)|Crea un control de animación con los estilos extendidos de Windows especificados y lo asocia a un `CAnimateCtrl` objeto.|  
|[CAnimateCtrl::IsPlaying](#isplaying)|Indica si se trata de un clip de Audio y vídeo intercalado (AVI).|  
|[CAnimateCtrl::Open](#open)|Abre un clip AVI desde un archivo o recurso y muestra el primer fotograma.|  
|[CAnimateCtrl::Play](#play)|Reproduce el clip AVI sin sonido.|  
|[CAnimateCtrl::Seek](#seek)|Muestra un solo fotograma seleccionado del clip AVI.|  
|[CAnimateCtrl::Stop](#stop)|Detiene la reproducción del clip AVI.|  
  
## <a name="remarks"></a>Comentarios  
 Este control (y, por tanto, la `CAnimateCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95, Windows 98 y Windows NT versión 3.51 y versiones posteriores.  
  
 Un control de animación es una ventana rectangular que muestra un clip en formato AVI (Audio y vídeo intercalado): el formato de audio y vídeo de Windows estándar. Un clip AVI es una serie de marcos de mapa de bits, como una película.  
  
 Los controles de animación pueden reproducir sólo los clips AVI sencillos. En concreto, los clips para reproducirse en un control de animación deben cumplir los siguientes requisitos:  
  
-   Debe haber exactamente una transmisión de vídeo y debe tener al menos un fotograma.  
  
-   Puede haber a lo sumo dos flujos en el archivo (normalmente la otra secuencia, si está presente, es una secuencia de audio, aunque el control de animación pasa por alto la información de audio).  
  
-   El clip debe ser sin comprimir o comprimir con compresión RLE8.  
  
-   Se permite ningún cambio de paleta en la secuencia de vídeo.  
  
 Puede agregar el clip AVI a la aplicación como un recurso de AVI o puede acompañar a la aplicación como un archivo AVI independiente.  
  
 Dado que el subproceso continúa ejecutándose mientras se muestra el clip AVI, un uso común de un control de animación es indicar la actividad del sistema durante una operación larga. Por ejemplo, el cuadro de diálogo Buscar del explorador de archivos muestra un icono de lupa móvil como el sistema busca un archivo.  
  
 Si creas un `CAnimateCtrl` objeto dentro de un cuadro de diálogo cuadro, o desde un recurso de cuadro de diálogo con el editor de cuadro de diálogo, se automáticamente destruirá cuando el usuario cierra el cuadro de diálogo.  
  
 Si creas un `CAnimateCtrl` objeto dentro de una ventana, es posible que deba destruirlo. Si crea la `CAnimateCtrl` objeto en la pila, se destruye automáticamente. Si crea el `CAnimateCtrl` objeto en el montón mediante el uso de la **nueva** función, debe llamar a **eliminar** en el objeto que lo destruirá. Si deriva una nueva clase de `CAnimateCtrl` y asigna memoria en esa clase, invalide el `CAnimateCtrl` destructor para deshacerse de las asignaciones.  
  
 Para obtener más información sobre el uso de `CAnimateCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CAnimateCtrl](../../mfc/using-canimatectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl  
 Construye un objeto `CAnimateCtrl`.  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a la [crear](#create) función de miembro para poder realizar cualquier otra operación en el objeto que se crea.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>  CAnimateCtrl::Close  
 Cierra el clip AVI que se abrió anteriormente en el control de animación (si existe) y lo quita de la memoria.  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="create"></a>  CAnimateCtrl::Create  
 Crea un control de animación y lo adjunta a un `CAnimateCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwStyle*  
 Especifica el estilo del control de animación. Aplicar cualquier combinación de las ventanas de estilos que se describe en la siguiente sección de comentarios y los estilos de control de animación se describen en [estilos de Control de animación](/windows/desktop/Controls/animation-control-styles) en el SDK de Windows.  
  
 *Rect*  
 Especifica la posición y el tamaño del control de animación. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
 *pParentWnd*  
 Especifica la ventana primaria del control de animación, normalmente un `CDialog`. No debe ser NULL.  
  
 *nID*  
 Especifica el identificador. del control de animación  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CAnimateCtrl` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de animación y lo adjunta a la `CAnimateCtrl` objeto.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de animación.  
  
- WS_CHILD siempre  
  
- WS_VISIBLE normalmente  
  
- WS_DISABLED rara vez  
  
 Si desea usar los estilos extendidos de windows con el control de animación, llame a [CreateEx](#createex) en lugar de `Create`.  
  
 Además de los estilos de ventana mencionados anteriormente, puede aplicar uno o varios de los estilos de control de animación a un control de animación. Consulte el SDK de Windows para obtener más información en [estilos de control de animación](/windows/desktop/Controls/animation-control-styles).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="createex"></a>  CAnimateCtrl::CreateEx  
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
 *dwExStyle*  
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.  
  
 *dwStyle*  
 Especifica el estilo del control de animación. Aplicar cualquier combinación de la ventana y estilos de control de animación se describen en [estilos de Control de animación](/windows/desktop/Controls/animation-control-styles) en el SDK de Windows.  
  
 *Rect*  
 Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.  
  
 *pParentWnd*  
 Un puntero a la ventana que es primario del control.  
  
 *nID*  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying  
 Indica si se trata de un clip de Audio y vídeo intercalado (AVI).  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se trata de un clip AVI; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [ACM_ISPLAYING](/windows/desktop/Controls/acm-isplaying) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="open"></a>  CAnimateCtrl::Open  
 Llame a esta función para abrir un clip AVI y mostrar su primer fotograma.  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFileName*  
 Un `CString` objeto o un puntero a una cadena terminada en null que contiene el nombre del archivo AVI o el nombre de un recurso AVI. Si este parámetro es NULL, el sistema cierra el clip AVI que se ha abierto previamente para el control de animación, si existe.  
  
 *nID*  
 El identificador de recurso AVI. Si este parámetro es NULL, el sistema cierra el clip AVI que se ha abierto previamente para el control de animación, si existe.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El recurso AVI se carga desde el módulo que creó el control de animación.  
  
 `Open` no admite el sonido de un clip AVI; puede abrir únicamente los clips AVI silenciosos.  
  
 Si el control de animación tiene el `ACS_AUTOPLAY` estilo, el control de animación automáticamente empezará a reproducirse el clip inmediatamente después de que lo abre. Reproducción del clip en segundo plano mientras el subproceso continúa la ejecución continuará. Cuando haya terminado el clip en reproducción, automáticamente se repetirá.  
  
 Si el control de animación tiene el `ACS_CENTER` estilo, el clip AVI estará centrado en el control y no cambiará el tamaño del control. Si el control de animación no tiene el `ACS_CENTER` estilo, el control se ajustará cuando se abre el clip AVI al tamaño de las imágenes en el clip AVI. La posición de la esquina superior izquierda del control no cambiará, solo el tamaño del control.  
  
 Si el control de animación tiene el `ACS_TRANSPARENT` estilo, el primer fotograma se dibuja utilizando un fondo transparente en lugar de especifica el color de fondo en el clip de animación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="play"></a>  CAnimateCtrl::Play  
 Llame a esta función para reproducir un clip AVI en un control de animación.  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>Parámetros  
 *nde*  
 Índice de base cero del marco donde se comienza a reproducir. Valor debe ser inferior a 65.536. Un valor de 0 significa que comienzan por el primer fotograma en el clip AVI.  
  
 *nPara*  
 Índice de base cero del marco de reproducción donde finaliza. Valor debe ser inferior a 65.536. Un valor de - 1 significa que termina con el último fotograma en el clip AVI.  
  
 *nRep*  
 Número de veces que se reproducirá el clip AVI. Un valor de - 1 significa que el archivo de reproducción indefinidamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El control de animación reproducirá el clip en segundo plano mientras el subproceso continúa ejecutando. Si el control de animación tiene `ACS_TRANSPARENT` estilo, el clip AVI se reproducirá con un fondo transparente, en lugar del color de fondo especificado en el clip de animación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="seek"></a>  CAnimateCtrl::Seek  
 Llame a esta función para mostrar estáticamente un solo fotograma del clip AVI.  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>Parámetros  
 *nPara*  
 Índice de base cero del marco para mostrar. Valor debe ser inferior a 65.536. Un valor de 0 significa que muestre el primer fotograma en el clip AVI. El valor -1 significa que mostrar el último fotograma en el clip AVI.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si el control de animación tiene `ACS_TRANSPARENT` estilo, el clip AVI se dibujará con un fondo transparente en lugar de especifica el color de fondo en el clip de animación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="stop"></a>  CAnimateCtrl::Stop  
 Llame a esta función para detener la reproducción un clip AVI en un control de animación.  
  
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

