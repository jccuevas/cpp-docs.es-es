---
title: Clase CPrintDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
dev_langs:
- C++
helpviewer_keywords:
- Print Setup dialog box
- Print dialog box
- CPrintDialog class
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: fe8b5a899169bf9dfd463278100384fde900a6a0
ms.lasthandoff: 02/24/2017

---
# <a name="cprintdialog-class"></a>Clase CPrintDialog
Encapsula los servicios proporcionados por el cuadro de diálogo común de Windows para imprimir.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPrintDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrintDialog::CPrintDialog](#cprintdialog)|Construye un objeto `CPrintDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora sin mostrar el cuadro de diálogo Imprimir.|  
|[CPrintDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|  
|[CPrintDialog::GetCopies](#getcopies)|Recupera el número de copias solicitadas.|  
|[CPrintDialog::GetDefaults](#getdefaults)|Recupera los valores predeterminados del dispositivo sin mostrar un cuadro de diálogo.|  
|[CPrintDialog::GetDeviceName](#getdevicename)|Recupera el nombre del dispositivo de impresora actualmente seleccionada.|  
|[CPrintDialog::GetDevMode](#getdevmode)|Recupera el `DEVMODE` estructura.|  
|[CPrintDialog::GetDriverName](#getdrivername)|Recupera el nombre del controlador de impresora seleccionada actualmente.|  
|[CPrintDialog::GetFromPage](#getfrompage)|Recupera la página de inicio del intervalo de impresión.|  
|[CPrintDialog::GetPortName](#getportname)|Recupera el nombre del puerto de impresora actualmente seleccionada.|  
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Recupera un identificador para el contexto de dispositivo de impresora.|  
|[CPrintDialog::GetToPage](#gettopage)|Recupera la página final del intervalo de impresión.|  
|[CPrintDialog::PrintAll](#printall)|Determina si se va a imprimir todas las páginas del documento.|  
|[CPrintDialog::PrintCollate](#printcollate)|Determina si se intercalan copias se solicitan.|  
|[CPrintDialog::PrintRange](#printrange)|Determina si se imprime sólo un intervalo de páginas especificado.|  
|[CPrintDialog::PrintSelection](#printselection)|Determina si se imprime sólo los elementos seleccionados actualmente.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrintDialog::m_pd](#m_pd)|Una estructura que se utiliza para personalizar una `CPrintDialog` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Cuadros de diálogo de impresión comunes proporcionan una manera fácil de implementar los cuadros de diálogo de impresión y configuración de impresión de una manera coherente con los estándares de Windows.  
  
> [!NOTE]
>  La `CPrintDialogEx` clase encapsula los servicios proporcionados por la hoja de propiedades de impresión de Windows 2000. Para obtener más información, consulte el [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) información general.  
  
 `CPrintDialog`de funcionalidad ha sido reemplazada por el de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), que está diseñada para proporcionar un cuadro de diálogo común para tanto el programa de instalación y configuración de página de la impresión.  
  
 Puede confiar en el marco de trabajo para controlar muchos aspectos del proceso de impresión de la aplicación. En este caso, el marco de trabajo muestra automáticamente el cuadro de diálogo comunes de Windows para la impresión. También puede tiene el identificador de framework imprimir de la aplicación y reemplazar el cuadro de diálogo de impresión comunes con su propio cuadro de diálogo Imprimir. Para obtener más información acerca de cómo utilizar el marco de trabajo para controlar las tareas de impresión, consulte el artículo [impresión](../../mfc/printing.md).  
  
 Si desea que la aplicación para controlar la impresión sin participación del marco de trabajo, puede usar el `CPrintDialog` clase "tal cual" con el constructor proporcionado, o puede derivar su propia clase de cuadro de diálogo de `CPrintDialog` y escribir un constructor para satisfacer sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como cuadros de diálogo MFC estándar, dado que se derivan de la clase `CCommonDialog`.  
  
 Para usar un `CPrintDialog` , primero cree el objeto utilizando la `CPrintDialog` constructor. Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la [m_pd](#m_pd) estructura para inicializar los valores de los controles del cuadro de diálogo. El `m_pd` estructura es de tipo [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843). Para obtener más información sobre esta estructura, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Si no se proporcionan sus propios controladores de `m_pd` para el **hDevMode** y **hDevNames** miembros, no olvide llamar a la función de Windows **GlobalFree** para estos identificadores cuando haya terminado con el cuadro de diálogo. Cuando se utiliza la implementación de instalación de impresión del marco de trabajo proporcionada por `CWinApp::OnFilePrintSetup`, no es necesario liberar estos identificadores. Los identificadores se mantienen por `CWinApp` y se liberan en `CWinApp`del destructor. Sólo es necesario liberar estos identificadores al usar `CPrintDialog` independiente.  
  
 Después de inicializar los controles de cuadro de diálogo, llame a la `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar las opciones de impresión. `DoModal`Devuelve si el usuario seleccionó Aceptar ( **IDOK**) o Cancelar ( **IDCANCEL**) botón.  
  
 Si `DoModal` devuelve **IDOK**, puede utilizar uno de `CPrintDialog`de funciones miembro para recuperar la información de entrada del usuario.  
  
 El `CPrintDialog::GetDefaults` función miembro es útil para recuperar los valores predeterminados actuales de impresora sin mostrar un cuadro de diálogo. Esta función miembro requiere ninguna interacción del usuario.  
  
 Puede utilizar las ventanas **CommDlgExtendedError** función para determinar si se produjo un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, consulte el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `CPrintDialog`se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3.1 y versiones posteriores de Windows.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CPrintDialog`, proporcionan una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Todos los mensajes sin procesar se deberían pasar a la clase base. No es necesario personalizar la función de enlace.  
  
 Para procesar el mismo mensaje de manera diferente dependiendo de si el cuadro de diálogo es Print o instalación de impresión, debe derivar una clase para cada cuadro de diálogo. También debe reemplazar el Windows **AttachOnSetup** función, que controla la creación de un nuevo cuadro de diálogo cuando se selecciona el botón Configurar impresión dentro de un cuadro de diálogo Imprimir.  
  
 Para obtener más información sobre el uso de `CPrintDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdlgs.h  
  
##  <a name="cprintdialog"></a>CPrintDialog::CPrintDialog  
 Crea el objeto de cuadro de diálogo de una impresión de Windows o la instalación de impresión.  
  
```  
CPrintDialog(
    BOOL bPrintSetupOnly,  
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bPrintSetupOnly`  
 Especifica si se muestra el cuadro de diálogo Imprimir de Windows estándar o el cuadro de diálogo Configuración de impresión. Establezca este parámetro en **TRUE** para mostrar el cuadro de diálogo instalación de impresión de Windows estándar. Establézcalo en **FALSE** para mostrar el cuadro de diálogo de impresión de Windows. Si `bPrintSetupOnly` es **FALSE**, un botón de opción de configuración de impresión se sigue mostrando en el cuadro de diálogo Imprimir.  
  
 `dwFlags`  
 Uno o más marcadores que puede usar para personalizar la configuración del cuadro de diálogo combinada mediante el operador OR bit a bit. Por ejemplo, el **PD_ALLPAGES** marca establece el intervalo de impresión predeterminado para todas las páginas del documento. Consulte la [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre estos indicadores.  
  
 `pParentWnd`  
 Puntero a la ventana primaria o propietaria del cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro sólo construye el objeto. Utilice la `DoModal` función miembro para mostrar el cuadro de diálogo.  
  
 Tenga en cuenta que al llamar al constructor con `bPrintSetupOnly` establecido en **FALSE**, **PD_RETURNDC** marca se utiliza automáticamente. Después de llamar a `DoModal`, `GetDefaults`, o `GetPrinterDC`, se devolverá una impresora DC en `m_pd.hDC`. Este controlador de dominio se debe liberar con una llamada a [DeleteObject](http://msdn.microsoft.com/library/windows/desktop/dd183533) el llamador de `CPrintDialog`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#174;](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC  
 Crea un contexto de dispositivo (DC) de impresora desde la [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) y [DEVNAMES](../../mfc/reference/devnames-structure.md) estructuras.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del contexto de dispositivo de impresora recién creada.  
  
### <a name="remarks"></a>Comentarios  
 Este controlador de dominio se supone que la impresora DC y cualquier otro obtenido previamente impresora que controladores de dominio se deben eliminar el usuario. Esta función se puede llamar y utiliza el controlador de dominio resultante, sin mostrar alguna vez el cuadro de diálogo Imprimir.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#106;](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]  
  
##  <a name="domodal"></a>CPrintDialog::DoModal  
 Muestra el cuadro de diálogo de impresión común de Windows y permite al usuario seleccionar varias opciones de impresión, como el número de copias, el intervalo de páginas, y si se deben intercalar copias.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **IDOK** o **IDCANCEL**. Si **IDCANCEL** es devuelto, llame a Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) función para determinar si se produjo un error.  
  
 **IDOK** y **IDCANCEL** son constantes que indican si el usuario seleccionó el botón Aceptar o Cancelar.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar las distintas opciones del cuadro de diálogo de impresión estableciendo los miembros de la `m_pd` estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Después de llamar a `DoModal`, puede llamar a otro miembro de funciones para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.  
  
 Tenga en cuenta que al llamar al constructor con `bPrintSetupOnly` establecido en **FALSE**, **PD_RETURNDC** marca se utiliza automáticamente. Después de llamar a `DoModal`, `GetDefaults`, o `GetPrinterDC`, se devolverá una impresora DC en `m_pd.hDC`. Este controlador de dominio se debe liberar con una llamada a [DeleteObject](http://msdn.microsoft.com/library/windows/desktop/dd183533) el llamador de `CPrintDialog`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::CreatePrinterDC](#createprinterdc).  
  
##  <a name="getcopies"></a>CPrintDialog::GetCopies  
 Recupera el número de copias solicitadas.  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de copias solicitadas.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a `DoModal` para recuperar el número de copias solicitadas.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdefaults"></a>CPrintDialog::GetDefaults  
 Recupera los valores predeterminados de dispositivo de la impresora predeterminada sin mostrar un cuadro de diálogo.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Los valores recuperados se colocan en el `m_pd` estructura.  
  
 En algunos casos, una llamada a esta función llama a la [constructor](#cprintdialog) de `CPrintDialog` con `bPrintSetupOnly` establecido en **FALSE**. En estos casos, una impresora DC y **hDevNames** y **hDevMode** (dos puntos de control se encuentran en la `m_pd` miembro de datos) se asignan automáticamente.  
  
 Si el constructor de `CPrintDialog` se llamó con `bPrintSetupOnly` establecido en **FALSE**, esta función no devolverá sólo **hDevNames** y **hDevMode** (ubicado en **m_pd.hDevNames** y **m_pd.hDevMode**) al llamador, pero también devolverá un DC de la impresora **m_pd.hDC**. Es responsabilidad del llamador para eliminar la impresora DC y llame a Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) (función) en los controladores cuando haya terminado con la `CPrintDialog` objeto.  
  
### <a name="example"></a>Ejemplo  
 Este fragmento de código obtiene el contexto de dispositivo de la impresora predeterminada e informa al usuario de la resolución de la impresora en puntos por pulgada. (Este atributo de capacidades de la impresora es a menudo sucesivo PPP.)  
  
 [!code-cpp[NVC_MFCDocView&#107;](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]  
  
##  <a name="getdevicename"></a>CPrintDialog::GetDeviceName  
 Recupera el nombre del dispositivo de impresora actualmente seleccionada.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre de la impresora seleccionada.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a [DoModal](#domodal) para recuperar el nombre de la impresora seleccionada, o después de llamar a [GetDefaults](#getdefaults) para recuperar los valores predeterminados del dispositivo actual de la impresora predeterminada. Utilice un puntero a la `CString` objeto devuelto por `GetDeviceName` como el valor de `lpszDeviceName` en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Ejemplo  
 Este fragmento de código muestra el nombre de usuario predeterminado impresora y el puerto que está conectado a, junto con el nombre de cola de impresión que utiliza la impresora. El código podría mostrar un cuadro de mensaje que dice, "la impresora predeterminada es HP LaserJet IIIP en \\\server\share mediante winspool.", por ejemplo.  
  
 [!code-cpp[NVC_MFCDocView&#108;](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]  
  
##  <a name="getdevmode"></a>CPrintDialog::GetDevMode  
 Recupera el `DEVMODE` estructura.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) estructuras de datos que contiene información acerca del entorno de un controlador de impresión y la inicialización del dispositivo. Debe desbloquear la memoria usada por esta estructura con Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) función, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar información sobre el dispositivo de impresión.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdrivername"></a>CPrintDialog::GetDriverName  
 Recupera el nombre del controlador de impresora seleccionada actualmente.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A `CString` especifica el nombre del controlador definido por el sistema.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del controlador de dispositivo de impresora definida por el sistema. Utilice un puntero a la `CString` objeto devuelto por `GetDriverName` como el valor de `lpszDriverName` en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getfrompage"></a>CPrintDialog::GetFromPage  
 Recupera la página de inicio del intervalo de impresión.  
  
```  
int GetFromPage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de página inicial en el intervalo de páginas que se imprimen.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a `DoModal` para recuperar el número de página inicial en el intervalo de páginas que se imprimen.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="getportname"></a>CPrintDialog::GetPortName  
 Recupera el nombre del puerto de impresora actualmente seleccionada.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre del puerto de impresora actualmente seleccionada.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del puerto de impresora actualmente seleccionada.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getprinterdc"></a>CPrintDialog::GetPrinterDC  
 Recupera un identificador para el contexto de dispositivo de impresora.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el contexto de dispositivo de impresora si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si el `bPrintSetupOnly` parámetro de la `CPrintDialog` constructor estaba **FALSE** (lo que indica que se muestra el cuadro de diálogo de impresión), a continuación, `GetPrinterDC` devuelve un identificador para el contexto de dispositivo de impresora. Se deben llamar a las ventanas de [DeleteObject](http://msdn.microsoft.com/library/windows/desktop/dd183533) función para eliminar el contexto de dispositivo cuando haya terminado de usarlo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#109;](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]  
  
##  <a name="gettopage"></a>CPrintDialog::GetToPage  
 Recupera la página final del intervalo de impresión.  
  
```  
int GetToPage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de página final en el intervalo de páginas que se imprimen.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a `DoModal` para recuperar el número de página final en el intervalo de páginas que se imprimen.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="m_pd"></a>CPrintDialog::m_pd  
 Una estructura cuyos miembros almacenan las características del objeto de cuadro de diálogo.  
  
```  
PRINTDLG& m_pd;  
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear un `CPrintDialog` objeto, puede usar `m_pd` para configurar varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro. Para obtener más información sobre la `m_pd` estructura, vea [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Si modifica el `m_pd` miembro de datos directamente, reemplazará cualquier comportamiento predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#111;](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]  
  
##  <a name="printall"></a>CPrintDialog::PrintAll  
 Determina si se va a imprimir todas las páginas del documento.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si están todas las páginas del documento que se imprimirá; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a `DoModal` para determinar si se imprimen todas las páginas del documento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="printcollate"></a>CPrintDialog::PrintCollate  
 Determina si se intercalan copias se solicitan.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el usuario selecciona la casilla Intercalar el cuadro de diálogo. en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a `DoModal` para determinar si la impresora debe intercalar todas las copias del documento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#110;](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]  
  
##  <a name="printrange"></a>CPrintDialog::PrintRange  
 Determina si se imprime sólo un intervalo de páginas especificado.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si sólo un intervalo de páginas en el documento se imprime; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a `DoModal` para determinar si desea imprimir sólo un intervalo de páginas del documento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="printselection"></a>CPrintDialog::PrintSelection  
 Determina si se imprime sólo los elementos seleccionados actualmente.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si solo los elementos seleccionados se imprimirán; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de llamar a `DoModal` para determinar si desea imprimir sólo los elementos seleccionados actualmente.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CPrintInfo (estructura)](../../mfc/reference/cprintinfo-structure.md)

