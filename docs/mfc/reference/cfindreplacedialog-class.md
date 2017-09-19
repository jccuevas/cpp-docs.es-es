---
title: Clase CFindReplaceDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
dev_langs:
- C++
helpviewer_keywords:
- text searches, replacing text
- text searches, CFindReplaceDialog class
- Find/Replace dialog box
- replacing text, CFindReplaceDialog class
- CFindReplaceDialog class
- replacing text
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 6ec814e3e96addfdadaaaa855260c8dbd495537e
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="cfindreplacedialog-class"></a>Clase CFindReplaceDialog
Le permite implementar los cuadros de diálogo Buscar/Reemplazar de cadena estándar en la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Llame a esta función para construir un `CFindReplaceDialog` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|Crea y muestra un `CFindReplaceDialog` cuadro de diálogo.|  
|[CFindReplaceDialog::FindNext](#findnext)|Llame a esta función para determinar si el usuario desea buscar la siguiente repetición de la cadena de búsqueda.|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|Llame a esta función para recuperar la cadena de búsqueda actual.|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Llame a esta función para recuperar el **FINDREPLACE** estructura en el controlador de mensajes registrados.|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Llame a esta función para recuperar la cadena de reemplazo actual.|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|Llame a esta función para determinar si el cuadro de diálogo está finalizando.|  
|[CFindReplaceDialog::MatchCase](#matchcase)|Llame a esta función para determinar si el usuario desea coincidir exactamente con el caso de la cadena de búsqueda.|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Llame a esta función para determinar si el usuario desea coincidir con solo palabras completas.|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Llame a esta función para determinar si el usuario desea que todas las apariciones de la cadena que se debe reemplazar.|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Llame a esta función para determinar si el usuario desea que la palabra actual que se debe reemplazar.|  
|[CFindReplaceDialog::SearchDown](#searchdown)|Llame a esta función para determinar si el usuario desea que la búsqueda para continuar en dirección descendente.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|Una estructura utilizada para personalizar un `CFindReplaceDialog` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 A diferencia de los otros Windows cuadros de diálogo comunes, `CFindReplaceDialog` objetos son no modales, lo que permite a los usuarios interactuar con otras ventanas mientras están en pantalla. Hay dos tipos de `CFindReplaceDialog` objetos: buscar cuadros de diálogo y cuadros de diálogo Buscar y reemplazar. Aunque los cuadros de diálogo permiten al usuario de entrada de búsqueda y las cadenas de búsqueda y reemplazo, no realizan alguna de la búsqueda o reemplazar las funciones. Debe agregarlas a la aplicación.  
  
 Para construir un `CFindReplaceDialog` objeto, utilice el constructor proporcionado (que no tiene ningún argumento). Puesto que se trata de un cuadro de diálogo no modal, asigne el objeto en el montón mediante el **nueva** operador, en lugar de en la pila.  
  
 Una vez un `CFindReplaceDialog` se ha construido el objeto, debe llamar a la [crear](#create) función de miembro para crear y mostrar el cuadro de diálogo.  
  
 Use la [m_fr](#m_fr) estructura para inicializar el cuadro de diálogo antes de llamar a **crear**. El `m_fr` estructura es de tipo [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Para obtener más información sobre esta estructura, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Fin de la ventana primaria para recibir una notificación de las solicitudes de buscar y reemplazar, debe utilizar las ventanas [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) funcionar y utilizar el [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) macros de mapa de mensajes en la ventana de marco que controla este mensaje registrado.  
  
 Puede determinar si el usuario ha decidido terminar el cuadro de diálogo con el `IsTerminating` función miembro.  
  
 `CFindReplaceDialog`se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3.1 y posteriores de Windows.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CFindReplaceDialog`, proporcione una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes sin procesar se deben pasar a la clase base.  
  
 Personalizar la función de enlace no es necesario.  
  
 Para obtener más información sobre el uso de `CFindReplaceDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdlgs.h  
  
##  <a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog  
 Construye un objeto `CFindReplaceDialog`.  
  
```  
CFindReplaceDialog();
```  
  
### <a name="remarks"></a>Comentarios  
 Dado que la `CFindReplaceDialog` objeto es un cuadro de diálogo no modal, debe crearlo en el montón mediante el uso de la `new` operador.  
  
 Durante la destrucción, el marco de trabajo intenta realizar una `delete this` en el puntero en el cuadro de diálogo. Si ha creado el cuadro de diálogo en la pila, el `this` puntero no existe y puede provocar un comportamiento indefinido.  
  
 Para obtener más información sobre la construcción de `CFindReplaceDialog` los objetos, vea la [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) información general. Use la [CFindReplaceDialog::Create](#create) función de miembro para mostrar el cuadro de diálogo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
##  <a name="create"></a>CFindReplaceDialog::Create  
 Crea y muestra una búsqueda o Buscar/Reemplazar cuadro objeto dialog, dependiendo del valor de `bFindDialogOnly`.  
  
```  
virtual BOOL Create(
    BOOL bFindDialogOnly,  
    LPCTSTR lpszFindWhat,  
    LPCTSTR lpszReplaceWith = NULL,  
    DWORD dwFlags = FR_DOWN,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bFindDialogOnly`  
 Establezca este parámetro en `TRUE` para mostrar una **buscar** cuadro de diálogo. Establézcalo en `FALSE` para mostrar una **Buscar/reemplazar** cuadro de diálogo.  
  
 `lpszFindWhat`  
 Puntero a la cadena de búsqueda de forma predeterminada, cuando aparezca el cuadro de diálogo. Si `NULL`, el cuadro de diálogo no contiene una cadena de búsqueda de forma predeterminada.  
  
 `lpszReplaceWith`  
 Puntero a la cadena de reemplazo de manera predeterminada, cuando aparezca el cuadro de diálogo. Si `NULL`, el cuadro de diálogo no contiene una cadena de reemplazo de forma predeterminada.  
  
 `dwFlags`  
 Una o varias marcas que puede usar para personalizar la configuración del cuadro de diálogo combinada mediante el operador OR bit a bit. El valor predeterminado es `FR_DOWN`, que especifica que la búsqueda se continuar en dirección descendente. Consulte la [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835) estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre estas marcas.  
  
 `pParentWnd`  
 Un puntero a la ventana primaria o propietaria del cuadro de diálogo. Esta es la ventana que va a recibir el mensaje especial que indica que se solicita una acción de buscar y reemplazar. Si `NULL`, se utiliza la ventana principal de la aplicación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se creó correctamente el objeto de cuadro de diálogo; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Fin de la ventana primaria para recibir una notificación de las solicitudes de buscar y reemplazar, debe utilizar las ventanas [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) función cuyo valor devuelto es un número de mensaje único para la instancia de la aplicación. La ventana de marco debe tener una entrada de mapa de mensajes que declara la función de devolución de llamada ( `OnFindReplace` en el ejemplo siguiente) que controla este mensaje registrado. El siguiente fragmento de código es un ejemplo de cómo hacer esto en una clase de ventana de marco denominada `CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView #171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView #172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 Dentro de su `OnFindReplace` función, interpretar las intenciones del usuario mediante el uso de la [CFindReplaceDialog::FindNext](#findnext) y [CFindReplaceDialog::IsTerminating](#isterminating) métodos y crear el código para las operaciones de buscar y reemplazar.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="findnext"></a>CFindReplaceDialog::FindNext  
 Llame a esta función desde la función de devolución de llamada para determinar si el usuario desea buscar la siguiente repetición de la cadena de búsqueda.  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario desea buscar la siguiente repetición de la cadena de búsqueda; en caso contrario es 0.  
  
##  <a name="getfindstring"></a>CFindReplaceDialog::GetFindString  
 Llame a esta función desde la función de devolución de llamada para recuperar la cadena predeterminada que buscar.  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cadena predeterminada para buscar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getnotifier"></a>CFindReplaceDialog::GetNotifier  
 Llame a esta función para recuperar un puntero al cuadro de diálogo Buscar y reemplazar actual.  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `lParam`  
 El **lparam** valor pasado a la ventana de marco **OnFindReplace** función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al cuadro de diálogo actual.  
  
### <a name="remarks"></a>Comentarios  
 Debe utilizarse dentro de la función de devolución de llamada para obtener acceso al cuadro de diálogo actual, llame a su miembro, funciones y acceso a la `m_fr` estructura.  
  
### <a name="example"></a>Ejemplo  
 Vea [CFindReplaceDialog::Create](#create) para obtener un ejemplo de cómo registrar el controlador OnFindReplace para recibir notificaciones en el cuadro de diálogo Buscar y reemplazar.  
  
 [!code-cpp[NVC_MFCDocView #69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString  
 Llame a esta función para recuperar la cadena de reemplazo actual.  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cadena predeterminada con la que se va a reemplazar cadenas se encuentra.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="isterminating"></a>CFindReplaceDialog::IsTerminating  
 Llame a esta función dentro de la función de devolución de llamada para determinar si el usuario ha decidido terminar el cuadro de diálogo.  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario ha decidido terminar el cuadro de diálogo; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si esta función devuelve un valor distinto de cero, debe llamar a la `DestroyWindow` función de miembro del cuadro de diálogo actual y establezca cualquier cuadro de diálogo cuadro variable de puntero a **NULL**. Si lo desea, también puede almacenar el texto de buscar y reemplazar el último elemento introducido y usarlo para inicializar el cuadro de diálogo Buscar/Reemplazar siguiente.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="m_fr"></a>CFindReplaceDialog::m_fr  
 Usar para personalizar un `CFindReplaceDialog` objeto.  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_fr`es una estructura de tipo [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Sus miembros almacenan las características del objeto de cuadro de diálogo. Después de crear un `CFindReplaceDialog` objeto, puede usar `m_fr` para modificar valores distintos en el cuadro de diálogo.  
  
 Para obtener más información sobre esta estructura, vea la **FINDREPLACE** estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="matchcase"></a>CFindReplaceDialog::MatchCase  
 Llame a esta función para determinar si el usuario desea coincidir exactamente con el caso de la cadena de búsqueda.  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario desea buscar apariciones de la cadena de búsqueda que coincidan exactamente con el caso de la cadena de búsqueda; en caso contrario es 0.  
  
##  <a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord  
 Llame a esta función para determinar si el usuario desea coincidir con solo palabras completas.  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario desea coincidir con solo las palabras completas de la cadena de búsqueda; en caso contrario es 0.  
  
##  <a name="replaceall"></a>CFindReplaceDialog::ReplaceAll  
 Llame a esta función para determinar si el usuario desea que todas las apariciones de la cadena que se debe reemplazar.  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario ha solicitado que reemplazará todas las cadenas que coinciden con la cadena de reemplazo; en caso contrario es 0.  
  
##  <a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent  
 Llame a esta función para determinar si el usuario desea que la palabra actual que se debe reemplazar.  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario ha solicitado que la cadena actualmente seleccionada se reemplaza con la cadena de reemplazo; en caso contrario es 0.  
  
##  <a name="searchdown"></a>CFindReplaceDialog::SearchDown  
 Llame a esta función para determinar si el usuario desea que la búsqueda para continuar en dirección descendente.  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el usuario desea que la búsqueda para continuar en dirección descendente; 0 si desea que la búsqueda para continuar en sentido ascendente.  
  
## <a name="see-also"></a>Vea también  
 [Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)  

