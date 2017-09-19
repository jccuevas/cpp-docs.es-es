---
title: Clase CBitmapButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
dev_langs:
- C++
helpviewer_keywords:
- buttons, bitmap
- CBitmapButton class
- bitmaps, button controls
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0b07f6b12e178d8e324313ea3b0f6de9ae7420c9
ms.openlocfilehash: 16d39cb380b75e6dcef71dda01626f120d5c12fb
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cbitmapbutton-class"></a>Clase CBitmapButton
Crea controles de botón de comando etiquetados con imágenes de mapa de bits en lugar de texto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBitmapButton : public CButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Construye un objeto `CBitmapButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBitmapButton:: Autoload](#autoload)|Asocia un botón en un cuadro de diálogo con un objeto de la `CBitmapButton` (clase), carga el bitmap(s) por nombre y cambia el tamaño del botón para ajustar el mapa de bits.|  
|[CBitmapButton:: LoadBitmaps](#loadbitmaps)|Inicializa el objeto cargar uno o más recursos de mapa de bits con nombre de archivo de recursos de la aplicación y asociar los mapas de bits para el objeto.|  
|[CBitmapButton::SizeToContent](#sizetocontent)|Cambia el tamaño del botón para acomodar el mapa de bits.|  
  
## <a name="remarks"></a>Comentarios  
 `CBitmapButton`los objetos contienen hasta cuatro mapas de bits que contienen imágenes para los distintos Estados que puede suponer un botón: (normal o), hacia abajo (o seleccionada), centrado y deshabilitado. El primer mapa de bits es necesario. los demás son opcionales.  
  
 Imágenes de mapa de bits del botón incluyen el borde alrededor de la imagen, así como la propia imagen. Normalmente, el borde juega un papel en que muestra el estado del botón. Por ejemplo, el mapa de bits para el estado de foco suele como uno para el estado de seguridad, pero con un margen del rectángulo de guiones desde el borde o una línea gruesa en el borde. El mapa de bits para el estado deshabilitado normalmente es similar a uno para el estado de seguridad, pero tiene menor contraste (como una selección de menú gris o atenuado).  
  
 Estos mapas de bits pueden ser de cualquier tamaño, pero se tratan como si fueran del mismo tamaño que el mapa de bits para el estado de seguridad.  
  
 Diversas aplicaciones exigen diferentes combinaciones de imágenes de mapa de bits:  
  
|Arriba|Verticalmente|Focused|Deshabilitado|Aplicación|  
|--------|----------|-------------|--------------|-----------------|  
|×||||Bitmap|  
|×|×|||Botón sin **WS_TABSTOP** estilo|  
|×|×|×|×|Botón de cuadro de diálogo con todos los Estados|  
|×|×|×||Botón de cuadro de diálogo con **WS_TABSTOP** estilo|  
  
 Al crear un control de botón de mapa de bits, establezca el **BS_OWNERDRAW** estilo para especificar que el botón está dibujado por el propietario. Esto hace que Windows envíe el `WM_MEASUREITEM` y `WM_DRAWITEM` mensajes para el botón; el marco de trabajo procesa estos mensajes y administra la apariencia del botón para usted.  
  
### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Para crear un control de botón de mapa de bits en el área de cliente de una ventana  
  
1.  Crear uno a cuatro imágenes de mapa de bits para el botón.  
  
2.  Construir la [CBitmapButton](#cbitmapbutton) objeto.  
  
3.  Llame a la [crear](../../mfc/reference/cbutton-class.md#create) función para crear el control de botón de Windows y adjuntarlo a la `CBitmapButton` objeto.  
  
4.  Llame a la [LoadBitmaps](#loadbitmaps) función miembro para cargar los recursos de mapa de bits una vez construido el botón de mapa de bits.  
  
### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Para incluir un control de botón de mapa de bits en un cuadro de diálogo  
  
1.  Crear uno a cuatro imágenes de mapa de bits para el botón.  
  
2.  Crear una plantilla de cuadro de diálogo con un botón dibujado por el propietario colocado donde desee que el botón de mapa de bits. No importa el tamaño del botón en la plantilla.  
  
3.  Establecer el título del botón en un valor como " **MYIMAGE**" y define un símbolo para el botón como **IDC_MYIMAGE**.  
  
4.  En el script de recursos de la aplicación, asignar a cada una de las imágenes creadas para el botón un identificador construido anexando una de las letras "U", "D", "F","o"X"(por hacia arriba, hacia abajo, centrado y deshabilitado) a la cadena utilizada para el título del botón en el paso 3. Para el título del botón " **MYIMAGE**," por ejemplo, los identificadores sería " **MYIMAGEU**," " **MYIMAGED**," " **MYIMAGEF**," y " **MYIMAGEX**." Le **debe** especificar el identificador de los mapas de bits entre comillas dobles. De lo contrario, el editor de recursos asignará a un número entero para el recurso y MFC se producirá un error al cargar la imagen.  
  
5.  En la clase de cuadro de diálogo de la aplicación (derivado de `CDialog`), agregue un `CBitmapButton` objeto miembro.  
  
6.  En el `CDialog` del objeto [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) rutinaria, llamada la `CBitmapButton` del objeto [AutoLoad](#autoload) funcione, utilizando como parámetros el identificador del control del botón y la `CDialog` del objeto **esto** puntero.  
  
 Si desea controlar los mensajes de notificación de Windows, como **BN_CLICKED**, enviada por un control de botón de mapa de bits a su elemento primario (normalmente una clase derivada de **CDialog)**, agregar a la `CDialog`-derivados de la función miembro para cada mensaje del controlador de mensajes y de entrada del objeto de un mapa de mensajes. Las notificaciones enviadas por un `CBitmapButton` objeto son los mismos que los enviados por un [CButton](../../mfc/reference/cbutton-class.md) objeto.  
  
 La clase [CToolBar](../../mfc/reference/ctoolbar-class.md) adopta un enfoque diferente para los botones de mapa de bits.  
  
 Para obtener más información sobre `CBitmapButton`, consulte [controles](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="autoload"></a>CBitmapButton:: Autoload  
 Asocia un botón en un cuadro de diálogo con un objeto de la `CBitmapButton` (clase), carga el bitmap(s) por nombre y cambia el tamaño del botón para ajustar el mapa de bits.  
  
```  
BOOL AutoLoad(
    UINT nID,  
    CWnd* pParent);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Identificador de control. del botón  
  
 `pParent`  
 Puntero al objeto al que pertenece el botón.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `AutoLoad` función para inicializar un botón dibujado por el propietario en el cuadro de diálogo como un botón de mapa de bits. Instrucciones para utilizar esta función se encuentran en la sección Comentarios para el `CBitmapButton` clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog&#75;](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]  
  
##  <a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton  
 Crea un objeto `CBitmapButton`.  
  
```  
CBitmapButton();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el C++ `CBitmapButton` objeto, llame a [CButton::Create](../../mfc/reference/cbutton-class.md#create) para crear el control de botón de Windows y adjuntarlo a la `CBitmapButton` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog&#57;](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]  
  
##  <a name="loadbitmaps"></a>CBitmapButton:: LoadBitmaps  
 Utilice esta función cuando desee cargar imágenes de mapa de bits que se identifican por sus nombres de recursos o los números de identificación, o cuando no se puede utilizar la `AutoLoad` de funcionar porque, por ejemplo, va a crear un botón de mapa de bits que no forma parte de un cuadro de diálogo.  
  
```  
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,  
    LPCTSTR lpszBitmapResourceSel = NULL,  
    LPCTSTR lpszBitmapResourceFocus = NULL,  
    LPCTSTR lpszBitmapResourceDisabled = NULL);

 
BOOL LoadBitmaps(
    UINT nIDBitmapResource,  
    UINT nIDBitmapResourceSel = 0,  
    UINT nIDBitmapResourceFocus = 0,  
    UINT nIDBitmapResourceDisabled = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszBitmapResource*  
 Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para normal de un botón de mapa de bits o "estado de up". Obligatorio.  
  
 *lpszBitmapResourceSel*  
 Señala a la cadena terminada en null que contiene el nombre del mapa de bits para un botón de mapa de bits está seleccionado o "estado inactivo". Puede ser **NULL**.  
  
 *lpszBitmapResourceFocus*  
 Apunta a la cadena terminada en null que contiene el nombre del mapa de bits para un botón de mapa de bits centra estado. Puede ser **NULL**.  
  
 *lpszBitmapResourceDisabled*  
 Estado de deshabilitado apunta a la cadena terminada en null que contiene el nombre del mapa de bits para un botón de mapa de bits. Puede ser **NULL**.  
  
 *nIDBitmapResource*  
 Especifica el número de identificador de recurso del recurso de mapa de bits para normal de un botón de mapa de bits o "estado de up". Obligatorio.  
  
 *nIDBitmapResourceSel*  
 Especifica el número de identificador de recurso del recurso de mapa de bits para un botón de mapa de bits está seleccionado o "estado inactivo". Puede ser 0.  
  
 *nIDBitmapResourceFocus*  
 Especifica el número de identificador de recurso del recurso de mapa de bits para el estado de foco de un botón de mapa de bits. Puede ser 0.  
  
 *nIDBitmapResourceDisabled*  
 Especifica el número de identificador de recurso del recurso de mapa de bits para el estado deshabilitado de un botón mapa de bits. Puede ser 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog&#58;](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]  
  
##  <a name="sizetocontent"></a>CBitmapButton::SizeToContent  
 Llame a esta función para cambiar el tamaño de un botón de mapa de bits para el tamaño del mapa de bits.  
  
```  
void SizeToContent();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog&#59;](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC CTRLTEST](../../visual-cpp-samples.md)   
 [CButton (clase)](../../mfc/reference/cbutton-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)


