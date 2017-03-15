---
title: Clase CHtmlEditCtrlBase | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditCtrlBase
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrlBase class
ms.assetid: e0cc74b4-8320-4570-b673-16c03d2ae266
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
ms.openlocfilehash: e5541025653cca908d5d0c7666a434aa3f81ab5b
ms.lasthandoff: 02/24/2017

---
# <a name="chtmleditctrlbase-class"></a>Clase CHtmlEditCtrlBase
Representa un componente de edición HTML.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class T> class CHtmlEditCtrlBase  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrlBase::AddToGlyphTable](#addtoglyphtable)|Agrega una entrada a la tabla de glifo, que especifica las imágenes que se muestran para las etiquetas específicas en modo de diseño.|  
|[CHtmlEditCtrlBase::Bold](#bold)|Alterna el estado de negrita del texto seleccionado.|  
|[CHtmlEditCtrlBase::Button](#button)|Sobrescribe un control de botón en la selección actual.|  
|[CHtmlEditCtrlBase::CheckBox](#checkbox)|Sobrescribe un control de casilla de verificación en la selección actual.|  
|[CHtmlEditCtrlBase::ClearSelection](#clearselection)|Borra la selección actual.|  
|[CHtmlEditCtrlBase::Copy](#copy)|Copia la selección actual en el Portapapeles.|  
|[CHtmlEditCtrlBase::Cut](#cut)|Copia la selección actual en el Portapapeles y, a continuación, se elimina.|  
|[CHtmlEditCtrlBase::Delete](#delete)|Elimina la selección actual.|  
|[CHtmlEditCtrlBase::DropDownBox](#dropdownbox)|Sobrescribe un control de selección de lista desplegable en la selección actual.|  
|[CHtmlEditCtrlBase::EmptyGlyphTable](#emptyglyphtable)|Quita todas las entradas de la tabla de glifo que oculta todas las imágenes que se muestran para las etiquetas en el modo de diseño.|  
|[CHtmlEditCtrlBase::ExecCommand](#execcommand)|Ejecuta un comando.|  
|[CHtmlEditCtrlBase::Font](#font)|Abre un cuadro de diálogo fuente para permitir al usuario cambiar el color del texto, fuente y tamaño de fuente de la selección actual.|  
|[CHtmlEditCtrlBase::GetAbsolutePosition](#getabsoluteposition)|Devuelve si la propiedad de posición de un elemento es "absoluta".|  
|[CHtmlEditCtrlBase::GetBackColor](#getbackcolor)|Recupera el color de fondo de la selección actual.|  
|[CHtmlEditCtrlBase::GetBlockFormat](#getblockformat)|Recupera la etiqueta de formato de bloque actual.|  
|[CHtmlEditCtrlBase::GetBlockFormatNames](#getblockformatnames)|Recupera las cadenas correspondientes a las etiquetas de formato de bloque disponible.|  
|[CHtmlEditCtrlBase::GetBookMark](#getbookmark)|Recupera el nombre de un delimitador de marcador.|  
|[CHtmlEditCtrlBase::GetDocument](#getdocument)|Recupera el objeto de documento.|  
|[CHtmlEditCtrlBase::GetDocumentHTML](#getdocumenthtml)|Recupera el código HTML del documento actual.|  
|[CHtmlEditCtrlBase::GetDocumentTitle](#getdocumenttitle)|Recupera el título del documento.|  
|[CHtmlEditCtrlBase::GetEvent](#getevent)|Recupera un puntero de interfaz al objeto de evento que contiene información relevante para el evento más reciente.|  
|[CHtmlEditCtrlBase::GetEventSrcElement](#geteventsrcelement)|Recupera el objeto que desencadenó el evento.|  
|[CHtmlEditCtrlBase::GetFontFace](#getfontface)|Recupera el nombre de fuente para la selección actual.|  
|[CHtmlEditCtrlBase::GetFontSize](#getfontsize)|Recupera el tamaño de fuente para la selección actual.|  
|[CHtmlEditCtrlBase::GetForeColor](#getforecolor)|Recupera el color de primer plano (texto) de la selección actual.|  
|[CHtmlEditCtrlBase::GetFrameZone](#getframezone)|Devuelve la zona de seguridad de la página actual en el explorador web.|  
|[CHtmlEditCtrlBase::GetIsDirty](#getisdirty)|Indica si se ha cambiado el documento HTML.|  
|[CHtmlEditCtrlBase::GetShowAlignedSiteTags](#getshowalignedsitetags)|Devuelve si se muestra un glifo para todos los elementos que tienen un **styleFloat** propiedad.|  
|[CHtmlEditCtrlBase::GetShowAllTags](#getshowalltags)|Devuelve si el control WebBrowser muestra los glifos para mostrar la ubicación de todas las etiquetas de un documento.|  
|[CHtmlEditCtrlBase::GetShowAreaTags](#getshowareatags)|Recupera si el control WebBrowser muestra un glifo para etiquetas de área.|  
|[CHtmlEditCtrlBase::GetShowBRTags](#getshowbrtags)|Recupera si el control WebBrowser muestra un glifo para br etiquetas.|  
|[CHtmlEditCtrlBase::GetShowCommentTags](#getshowcommenttags)|Recupera si el control WebBrowser muestra un glifo para etiquetas de comentario.|  
|[CHtmlEditCtrlBase::GetShowMiscTags](#getshowmisctags)|Recupera si el control WebBrowser muestra todas las etiquetas que se muestran en Microsoft Internet Explorer 4.0.|  
|[CHtmlEditCtrlBase::GetShowScriptTags](#getshowscripttags)|Recupera si el control WebBrowser muestra un glifo para todas las etiquetas de script.|  
|[CHtmlEditCtrlBase::GetShowStyleTags](#getshowstyletags)|Recupera si el control WebBrowser muestra un glifo para todas las etiquetas de estilo.|  
|[CHtmlEditCtrlBase::GetShowUnknownTags](#getshowunknowntags)|Recupera si el control WebBrowser muestra un glifo para todas las etiquetas desconocidos.|  
|[CHtmlEditCtrlBase::HorizontalLine](#horizontalline)|Sobrescribe una línea horizontal en la selección actual.|  
|[CHtmlEditCtrlBase::HyperLink](#hyperlink)|Inserta un hipervínculo en la selección actual.|  
|[CHtmlEditCtrlBase::IE50Paste](#ie50paste)|Realiza una operación de pegar compatible con Microsoft Internet Explorer 5.|  
|[CHtmlEditCtrlBase::Iframe](#iframe)|Sobrescribe un marco en la selección actual.|  
|[CHtmlEditCtrlBase::Image](#image)|Sobrescribe una imagen en la selección actual.|  
|[CHtmlEditCtrlBase::Indent](#indent)|Aumenta la sangría del texto seleccionado en el incremento de una sangría.|  
|[CHtmlEditCtrlBase::InsFieldSet](#insfieldset)|Sobrescribe un cuadro en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputButton](#insinputbutton)|Sobrescribe un control de botón en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputHidden](#insinputhidden)|Inserta un control oculto en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputImage](#insinputimage)|Sobrescribe un control de imagen en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputPassword](#insinputpassword)|Sobrescribe un control de contraseña en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputReset](#insinputreset)|Sobrescribe un control de restablecimiento de la selección actual.|  
|[CHtmlEditCtrlBase::InsInputSubmit](#insinputsubmit)|Sobrescribe un control enviar en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputUpload](#insinputupload)|Sobrescribe un control de carga de archivos en la selección actual.|  
|[CHtmlEditCtrlBase::Is1DElement](#is1delement)|Determina si un elemento se coloca estáticamente.|  
|[CHtmlEditCtrlBase::Is2DElement](#is2delement)|Determina si un elemento se coloca absolutamente.|  
|[CHtmlEditCtrlBase::Italic](#italic)|Alterna la selección actual entre cursiva y algunos.|  
|[CHtmlEditCtrlBase::JustifyCenter](#justifycenter)|Centra el bloque del formato en que se encuentra la selección actual.|  
|[CHtmlEditCtrlBase::JustifyLeft](#justifyleft)|Justifica a la izquierda el bloque del formato en que se encuentra la selección actual.|  
|[CHtmlEditCtrlBase::JustifyRight](#justifyright)|Justifica a la derecha del bloque del formato en que se encuentra la selección actual.|  
|[CHtmlEditCtrlBase::ListBox](#listbox)|Sobrescribe un control de selección de cuadro de lista en la selección actual.|  
|[CHtmlEditCtrlBase::Marquee](#marquee)|Sobrescribe un recuadro vacío en la selección actual.|  
|[CHtmlEditCtrlBase::NewDocument](#newdocument)|Crea un nuevo documento.|  
|[CHtmlEditCtrlBase::OrderList](#orderlist)|Alterna la selección actual entre una lista ordenada y un bloque de formato normal.|  
|[CHtmlEditCtrlBase::Outdent](#outdent)|Disminuye en un incremento la sangría del bloque de formato en que se encuentra la selección actual.|  
|[CHtmlEditCtrlBase::Paragraph](#paragraph)|Sobrescribe un salto de línea en la selección actual.|  
|[CHtmlEditCtrlBase::Paste](#paste)|Sobrescribe el contenido del Portapapeles en la selección actual.|  
|[CHtmlEditCtrlBase::PrintDocument](#printdocument)|Imprime el documento actual.|  
|[CHtmlEditCtrlBase::PrintPreview](#printpreview)|Abre la ventana de vista previa de impresión del documento actual utilizando la plantilla predeterminada de la vista previa de impresión o una plantilla personalizada.|  
|[CHtmlEditCtrlBase::QueryStatus](#querystatus)|Llame a este método para consultar el estado de comandos.|  
|[CHtmlEditCtrlBase::RadioButton](#radiobutton)|Sobrescribe un control de radio en la selección actual.|  
|[CHtmlEditCtrlBase::RefreshDocument](#refreshdocument)|Actualiza el documento actual.|  
|[CHtmlEditCtrlBase::RemoveFormat](#removeformat)|Quita las etiquetas de formato de la selección actual.|  
|[CHtmlEditCtrlBase::SaveAs](#saveas)|Guarda la página Web actual en un archivo.|  
|[CHtmlEditCtrlBase::SelectAll](#selectall)|Selecciona todo el documento.|  
|[CHtmlEditCtrlBase::Set2DPosition](#set2dposition)|Permite mover arrastrando elementos con posición absoluta.|  
|[CHtmlEditCtrlBase::SetAbsolutePosition](#setabsoluteposition)|Establece la propiedad de posición de un elemento "absoluto" o "estático".|  
|[CHtmlEditCtrlBase::SetAtomicSelection](#setatomicselection)|Establecer el modo de selección atómica.|  
|[CHtmlEditCtrlBase::SetAutoURLDetectMode](#setautourldetectmode)|Activa la detección automática de dirección URL y desactiva.|  
|[CHtmlEditCtrlBase::SetBackColor](#setbackcolor)|Establece el color de fondo de la selección actual.|  
|[CHtmlEditCtrlBase::SetBlockFormat](#setblockformat)|Establece la etiqueta de formato de bloque actual.|  
|[CHtmlEditCtrlBase::SetBookMark](#setbookmark)|Crea un delimitador de marcador para el punto de inserción o la selección actual.|  
|[CHtmlEditCtrlBase::SetCSSEditingLevel](#setcsseditinglevel)|Selecciona el nivel CSS (partir de CSS1 o CSS2) el editor admitirá, si existe.|  
|[CHtmlEditCtrlBase::SetDefaultComposeSettings](#setdefaultcomposesettings)|Configuración de redacción de este método para establecer el valor predeterminado de llamada.|  
|[CHtmlEditCtrlBase::SetDesignMode](#setdesignmode)|Establecer el modo de diseño.|  
|[CHtmlEditCtrlBase::SetDisableEditFocusUI](#setdisableeditfocusui)|Deshabilita el borde sombreado y alrededor de un elemento que tiene el foco de la edición.|  
|[CHtmlEditCtrlBase::SetDocumentHTML](#setdocumenthtml)|Establece el código HTML del documento actual.|  
|[CHtmlEditCtrlBase::SetFontFace](#setfontface)|Establece la fuente para la selección actual.|  
|[CHtmlEditCtrlBase::SetFontSize](#setfontsize)|Establece el tamaño de fuente para la selección actual.|  
|[CHtmlEditCtrlBase::SetForeColor](#setforecolor)|Establece el color de primer plano (texto) de la selección actual.|  
|[CHtmlEditCtrlBase::SetIE5PasteMode](#setie5pastemode)|Establece la operación de pegar para ser compatible con Microsoft Internet Explorer 5.|  
|[CHtmlEditCtrlBase::SetLiveResize](#setliveresize)|Hace que el control WebBrowser actualizar la apariencia de un elemento continuamente durante una operación de cambio de tamaño o mover.|  
|[CHtmlEditCtrlBase::SetMultiSelect](#setmultiselect)|Permite la selección múltiple.|  
|[CHtmlEditCtrlBase::SetOverrideCursor](#setoverridecursor)|Comandos WebBrowser nunca para cambiar el puntero del mouse.|  
|[CHtmlEditCtrlBase::SetOverwriteMode](#setoverwritemode)|Activa o desactiva el modo de entrada de texto entre insertar y sobrescribir.|  
|[CHtmlEditCtrlBase::SetRespectVisInDesign](#setrespectvisindesign)|Oculta los elementos invisibles en modo de diseño.|  
|[CHtmlEditCtrlBase::SetShowAlignedSiteTags](#setshowalignedsitetags)|Muestra un glifo para todos los elementos que tienen un **styleFloat** propiedad.|  
|[CHtmlEditCtrlBase::SetShowAllTags](#setshowalltags)|Muestra los glifos para mostrar la ubicación de todas las etiquetas de un documento.|  
|[CHtmlEditCtrlBase::SetShowAreaTags](#setshowareatags)|Muestra un glifo para todas las etiquetas de área.|  
|[CHtmlEditCtrlBase::SetShowBRTags](#setshowbrtags)|Muestra un glifo para todas las etiquetas br.|  
|[CHtmlEditCtrlBase::SetShowCommentTags](#setshowcommenttags)|Muestra un glifo para todas las etiquetas de comentario.|  
|[CHtmlEditCtrlBase::SetShowMiscTags](#setshowmisctags)|Muestra todas las etiquetas que se muestran en Microsoft Internet Explorer 4.0.|  
|[CHtmlEditCtrlBase::SetShowScriptTags](#setshowscripttags)|Muestra un glifo para todas las etiquetas de script.|  
|[CHtmlEditCtrlBase::SetShowStyleTags](#setshowstyletags)|Muestra un glifo para todas las etiquetas de estilo.|  
|[CHtmlEditCtrlBase::SetShowUnknownTags](#setshowunknowntags)|Muestra un glifo para todas las etiquetas desconocidos.|  
|[CHtmlEditCtrlBase::TextArea](#textarea)|Sobrescribe un control de entrada de texto de varias líneas en la selección actual.|  
|[CHtmlEditCtrlBase::TextBox](#textbox)|Sobrescribe un control de texto en la selección actual.|  
|[CHtmlEditCtrlBase::UnBookmark](#unbookmark)|Quita los marcadores de la selección actual.|  
|[CHtmlEditCtrlBase::Underline](#underline)|Alterna la selección actual entre subrayado y no subrayado.|  
|[CHtmlEditCtrlBase::Unlink](#unlink)|Quita cualquier hipervínculo de la selección actual.|  
|[CHtmlEditCtrlBase::UnorderList](#unorderlist)|Alterna la selección actual entre una lista ordenada y un bloque de formato normal.|  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El nombre de la clase derivada.  
  
## <a name="remarks"></a>Comentarios  
 **CHtmlEditCtrlBase** proporciona funciones miembro para HTML de WebBrowser Editar comandos, como [negrita](#bold). (Como alternativa, puede llamar a [ExecCommand](#execcommand) para ejecutar el **IDM_BOLD** comando.)  
  
 **CHtmlEditCtrlBase** no está diseñado para mantenerse en forma autónoma. Está diseñado para ser una clase base para las clases derivadas que exponen la funcionalidad de WebBrowser de edición de HTML (consulte [CHtmlEditCtrl](../../mfc/reference/chtmleditctrl-class.md) y [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CHtmlEditCtrlBase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxhtml.h  
  
##  <a name="a-nameaddtoglyphtablea--chtmleditctrlbaseaddtoglyphtable"></a><a name="addtoglyphtable"></a>CHtmlEditCtrlBase::AddToGlyphTable  
 Agrega una entrada a la tabla de glifo, que especifica las imágenes que se muestran para las etiquetas específicas en modo de diseño.  
  
```  
HRESULT AddToGlyphTable(
    LPCTSTR szTag,  
    LPCTSTR szImgUrl,  
    unsigned short nTagType,  
    unsigned short nAlignment,  
    unsigned short nPosInfo,  
    unsigned short nDirection,  
    unsigned int nImgWidth,  
    unsigned int nImgHeight) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szTag`  
 El nombre de etiqueta (por ejemplo, "P" o "tabla").  
  
 *szImgUrl*  
 La URL de la imagen.  
  
 *nTagType*  
 Tipo de etiqueta: 0 significa que la imagen es de sólo la etiqueta de apertura. 1 significa que la imagen es de sólo la etiqueta de cierre. 2 significa que la imagen es para las etiquetas de apertura y cierre. Solo etiquetas como comentario y br deben agregarse con el tipo de etiqueta establecido en 0.  
  
 *nAlignment*  
 Alineación (solo elementos rectangulares): este parámetro indica que la imagen es para un elemento con un atributo de alineación. Left = 0, center = 1, derecha = 2 y undefined = 3. Izquierda, derecha o centro atributos deben establecerse explícitamente en el elemento.  
  
 *nPosInfo*  
 Información de posición. Determina qué estilos en cascada hojas de valor de posición (CSS) se aplica el glifo, donde estático posicionamiento = 0, posicionamiento absoluto = 1, posición relativa = 2 y todos = 3. Este campo le permite especificar un glifo para una etiqueta cuando no se encuentra y otro glifo para mostrar un punto de anclaje cuando se coloca la etiqueta.  
  
 *nDirection*  
 La dirección. Este parámetro especifica la imagen de una etiqueta basada en el orden de lectura del idioma actual. 0 especifica de izquierda a derecha, 1 especifica derecha a izquierda, 2 especifica arriba a abajo, 3 especifica abajo a arriba y especifica 4 todos. Normalmente, se establece este campo en 4.  
  
 *nImgWidth*  
 El ancho de la imagen en píxeles.  
  
 *nImgHeight*  
 El alto de la imagen en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los parámetros, vea "Formato de cadena de glifo tabla" en [glifos de edición usando](https://msdn.microsoft.com/library/aa969614.aspx).  
  
 Este método envía el [IDM_ADDTOGLYPHTABLE identificador de comando](https://msdn.microsoft.com/library/aa769891.aspx) para el control WebBrowser.  
  
##  <a name="a-namebolda--chtmleditctrlbasebold"></a><a name="bold"></a>CHtmlEditCtrlBase::Bold  
 Alterna el estado de negrita del texto seleccionado.  
  
```  
HRESULT Bold() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_BOLD identificador de comando](https://msdn.microsoft.com/library/aa769861.aspx) para el control WebBrowser.  
  
##  <a name="a-namebuttona--chtmleditctrlbasebutton"></a><a name="button"></a>CHtmlEditCtrlBase::Button  
 Sobrescribe un control de botón en la selección actual.  
  
```  
HRESULT Button(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del control de botón.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_BUTTON identificador de comando](https://msdn.microsoft.com/library/aa769966.aspx) para el control WebBrowser.  
  
##  <a name="a-namecheckboxa--chtmleditctrlbasecheckbox"></a><a name="checkbox"></a>CHtmlEditCtrlBase::CheckBox  
 Sobrescribe un control de casilla de verificación en la selección actual.  
  
```  
HRESULT CheckBox(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del control de casilla de verificación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_CHECKBOX identificador de comando](https://msdn.microsoft.com/library/aa769972.aspx) para el control WebBrowser.  
  
##  <a name="a-nameclearselectiona--chtmleditctrlbaseclearselection"></a><a name="clearselection"></a>CHtmlEditCtrlBase::ClearSelection  
 Borra la selección actual.  
  
```  
HRESULT ClearSelection() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_CLEARSELECTION identificador de comando](https://msdn.microsoft.com/library/aa770038.aspx) para el control WebBrowser.  
  
##  <a name="a-namecopya--chtmleditctrlbasecopy"></a><a name="copy"></a>CHtmlEditCtrlBase::Copy  
 Copia la selección actual en el Portapapeles.  
  
```  
HRESULT Copy() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_COPY identificador de comando](https://msdn.microsoft.com/library/aa769872.aspx) para el control WebBrowser.  
  
##  <a name="a-namecuta--chtmleditctrlbasecut"></a><a name="cut"></a>CHtmlEditCtrlBase::Cut  
 Copia la selección actual en el Portapapeles y, a continuación, se elimina.  
  
```  
HRESULT Cut() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_CUT identificador de comando](https://msdn.microsoft.com/library/aa769875.aspx) para el control WebBrowser.  
  
##  <a name="a-namedeletea--chtmleditctrlbasedelete"></a><a name="delete"></a>CHtmlEditCtrlBase::Delete  
 Elimina la selección actual.  
  
```  
HRESULT Delete() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_DELETE identificador de comando](https://msdn.microsoft.com/library/aa769876.aspx) para el control WebBrowser.  
  
##  <a name="a-namedropdownboxa--chtmleditctrlbasedropdownbox"></a><a name="dropdownbox"></a>CHtmlEditCtrlBase::DropDownBox  
 Sobrescribe un control de selección de lista desplegable en la selección actual.  
  
```  
HRESULT DropDownBox(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del control de lista desplegable.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_DROPDOWNBOX identificador de comando](https://msdn.microsoft.com/library/aa769984.aspx) para el control WebBrowser.  
  
##  <a name="a-nameemptyglyphtablea--chtmleditctrlbaseemptyglyphtable"></a><a name="emptyglyphtable"></a>CHtmlEditCtrlBase::EmptyGlyphTable  
 Quita todas las entradas de la tabla de glifo que oculta todas las imágenes que se muestran para las etiquetas en el modo de diseño.  
  
```  
HRESULT EmptyGlyphTable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_EMPTYGLYPHTABLE identificador de comando](https://msdn.microsoft.com/library/aa769907.aspx) para el control WebBrowser.  
  
##  <a name="a-nameexeccommanda--chtmleditctrlbaseexeccommand"></a><a name="execcommand"></a>CHtmlEditCtrlBase::ExecCommand  
 Ejecuta un comando.  
  
```  
HRESULT ExecCommand(
    long cmdID,  
    long cmdExecOpt,  
    VARIANT* pInVar = NULL,  
    VARIANT* pOutVar = NULL) const;  
  
HRESULT ExecCommand(
    const GUID* pGuid,  
    long cmdID,  
    long cmdExecOpt,  
    VARIANT* pInVar = NULL,  
    VARIANT* pOutVar = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 El identificador de comando que se va a ejecutar. Para obtener una lista, consulte [identificadores de comandos de MSHTML](https://msdn.microsoft.com/library/aa741315.aspx).  
  
 `cmdExecOpt`  
 Valores tomados de la [OLECMDEXECOPT](http://msdn.microsoft.com/library/windows/desktop/ms683930) enumeración, que se describe cómo el objeto debe ejecutar el comando.  
  
 *pInVar*  
 Los argumentos de entrada.  
  
 *pOutVar*  
 La salida del comando.  
  
 *pGuid*  
 El GUID del grupo de comandos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método proporciona la funcionalidad de [IOleCommandTarget::Exec](http://msdn.microsoft.com/library/windows/desktop/ms690300).  
  
##  <a name="a-namefonta--chtmleditctrlbasefont"></a><a name="font"></a>CHtmlEditCtrlBase::Font  
 Abre un cuadro de diálogo fuente para permitir al usuario cambiar el color del texto, fuente y tamaño de fuente de la selección actual.  
  
```  
HRESULT Font() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_FONT identificador de comando](https://msdn.microsoft.com/library/aa769913.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetabsolutepositiona--chtmleditctrlbasegetabsoluteposition"></a><a name="getabsoluteposition"></a>CHtmlEditCtrlBase::GetAbsolutePosition  
 Devuelve si la propiedad de posición de un elemento es "absoluta".  
  
```  
HRESULT GetAbsolutePosition(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si la propiedad de posición del elemento se establece en "absoluta".  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_ABSOLUTE_POSITION identificador de comando](https://msdn.microsoft.com/library/aa769889.aspx).  
  
##  <a name="a-namegetbackcolora--chtmleditctrlbasegetbackcolor"></a><a name="getbackcolor"></a>CHtmlEditCtrlBase::GetBackColor  
 Recupera el color de fondo de la selección actual.  
  
```  
HRESULT GetBackColor(int& nColor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nColor`  
 Color de fondo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_BACKCOLOR identificador de comando](https://msdn.microsoft.com/library/aa769858.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetblockformata--chtmleditctrlbasegetblockformat"></a><a name="getblockformat"></a>CHtmlEditCtrlBase::GetBlockFormat  
 Recupera la etiqueta de formato de bloque actual.  
  
```  
HRESULT GetBlockFormat(CString& strFormat) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *strFormat*  
 La etiqueta de formato de bloque actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_BLOCKFMT identificador de comando](https://msdn.microsoft.com/library/aa769883.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetblockformatnamesa--chtmleditctrlbasegetblockformatnames"></a><a name="getblockformatnames"></a>CHtmlEditCtrlBase::GetBlockFormatNames  
 Recupera las cadenas correspondientes a las etiquetas de formato de bloque disponible.  
  
```  
HRESULT GetBlockFormatNames(CStringArray& sa) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *SA*  
 Las etiquetas de formato de bloque disponible, como una matriz de cadenas.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_GETBLOCKFMTS el Id. de comando](https://msdn.microsoft.com/library/aa769884.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetbookmarka--chtmleditctrlbasegetbookmark"></a><a name="getbookmark"></a>CHtmlEditCtrlBase::GetBookMark  
 Recupera el nombre de un delimitador de marcador.  
  
```  
HRESULT GetBookMark(CString& strAnchor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *strAnchor*  
 El nombre de un delimitador de marcador.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_BOOKMARK identificador de comando](https://msdn.microsoft.com/library/aa769873.aspx).  
  
##  <a name="a-namegetdocumenta--chtmleditctrlbasegetdocument"></a><a name="getdocument"></a>CHtmlEditCtrlBase::GetDocument  
 Recupera el objeto de documento.  
  
```  
HRESULT GetDocument(IHTMLDocument2** ppDoc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `ppDoc`  
 El objeto document.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namegetdocumenthtmla--chtmleditctrlbasegetdocumenthtml"></a><a name="getdocumenthtml"></a>CHtmlEditCtrlBase::GetDocumentHTML  
 Recupera el código HTML del documento actual.  
  
```  
HRESULT GetDocumentHTML(CString& szHTML) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szHTML`  
 El código HTML.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namegetdocumenttitlea--chtmleditctrlbasegetdocumenttitle"></a><a name="getdocumenttitle"></a>CHtmlEditCtrlBase::GetDocumentTitle  
 Recupera el título del documento.  
  
```  
HRESULT GetDocumentTitle(CString& szTitle) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *szTitle*  
 El título del documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namegeteventa--chtmleditctrlbasegetevent"></a><a name="getevent"></a>CHtmlEditCtrlBase::GetEvent  
 Recupera un puntero de interfaz al objeto de evento que contiene información relevante para el evento más reciente.  
  
```  
HRESULT GetEvent(IHTMLEventObj** ppEventObj) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `ppEventObj`  
 El objeto de evento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namegeteventsrcelementa--chtmleditctrlbasegeteventsrcelement"></a><a name="geteventsrcelement"></a>CHtmlEditCtrlBase::GetEventSrcElement  
 Recupera el objeto que desencadenó el evento.  
  
```  
HRESULT GetEventSrcElement(IHTMLElement** ppSrcElement) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *ppSrcElement*  
 El elemento que desencadenó el evento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namegetfontfacea--chtmleditctrlbasegetfontface"></a><a name="getfontface"></a>CHtmlEditCtrlBase::GetFontFace  
 Recupera el nombre de fuente para la selección actual.  
  
```  
HRESULT GetFontFace(CString& strFace) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `strFace`  
 El nombre de la fuente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Si la selección actual usa más de una fuente `strFace` será una cadena vacía.  
  
 Este método envía el [IDM_FONTNAME identificador de comando](https://msdn.microsoft.com/library/aa769880.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetfontsizea--chtmleditctrlbasegetfontsize"></a><a name="getfontsize"></a>CHtmlEditCtrlBase::GetFontSize  
 Recupera el tamaño de fuente para la selección actual.  
  
```  
HRESULT GetFontSize(short& nSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSize`  
 El tamaño de fuente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño de fuente HTML (1-7). Devuelve 0 si la selección contiene varios tamaños de fuente.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_FONTSIZE identificador de comando](https://msdn.microsoft.com/library/aa769881.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetforecolora--chtmleditctrlbasegetforecolor"></a><a name="getforecolor"></a>CHtmlEditCtrlBase::GetForeColor  
 Recupera el color de primer plano (texto) de la selección actual.  
  
```  
HRESULT GetForeColor(int& nColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `nColor`  
 El color de primer plano.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_FORECOLOR identificador de comando](https://msdn.microsoft.com/library/aa769882.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetframezonea--chtmleditctrlbasegetframezone"></a><a name="getframezone"></a>CHtmlEditCtrlBase::GetFrameZone  
 Devuelve la zona de seguridad de la página actual en el explorador web.  
  
```  
HRESULT GetFrameZone(short& nZone) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *nZone*  
 La zona de seguridad.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_GETFRAMEZONE identificador de comando](https://msdn.microsoft.com/library/aa769916.aspx) para el control WebBrowser.  
  
##  <a name="a-namegetisdirtya--chtmleditctrlbasegetisdirty"></a><a name="getisdirty"></a>CHtmlEditCtrlBase::GetIsDirty  
 Indica si se ha cambiado el documento HTML.  
  
```  
HRESULT GetIsDirty() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Indica si el documento ha cambiado. `GetIsDirty`Devuelve un `HRESULT` de [IPersistStorage::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910).  
  
##  <a name="a-namegetshowalignedsitetagsa--chtmleditctrlbasegetshowalignedsitetags"></a><a name="getshowalignedsitetags"></a>CHtmlEditCtrlBase::GetShowAlignedSiteTags  
 Devuelve si se muestra un glifo para todos los elementos que tienen un **styleFloat** propiedad.  
  
```  
HRESULT GetShowAlignedSiteTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si se muestra un glifo para todos los elementos que tienen un **styleFloat** propiedad; false si ningún glifo se muestra.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWALIGNEDSITETAGS identificador de comando](https://msdn.microsoft.com/library/aa769947.aspx).  
  
##  <a name="a-namegetshowalltagsa--chtmleditctrlbasegetshowalltags"></a><a name="getshowalltags"></a>CHtmlEditCtrlBase::GetShowAllTags  
 Devuelve si el control WebBrowser muestra los glifos para mostrar la ubicación de todas las etiquetas de un documento.  
  
```  
HRESULT GetShowAllTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra los glifos para mostrar la ubicación de todas las etiquetas en un documento. False si no es así.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWALLTAGS identificador de comando](https://msdn.microsoft.com/library/aa769948.aspx).  
  
##  <a name="a-namegetshowareatagsa--chtmleditctrlbasegetshowareatags"></a><a name="getshowareatags"></a>CHtmlEditCtrlBase::GetShowAreaTags  
 Recupera si el control WebBrowser muestra un glifo para etiquetas de área.  
  
```  
HRESULT GetShowAreaTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra un glifo para etiquetas de área, false si no es así.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWAREATAGS identificador de comando](https://msdn.microsoft.com/library/aa769949.aspx).  
  
##  <a name="a-namegetshowbrtagsa--chtmleditctrlbasegetshowbrtags"></a><a name="getshowbrtags"></a>CHtmlEditCtrlBase::GetShowBRTags  
 Recupera si el control WebBrowser muestra un glifo para br etiquetas.  
  
```  
HRESULT GetShowBRTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra un glifo para etiquetas br, false si no lo está.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWWBRTAGS identificador de comando](https://msdn.microsoft.com/library/aa769956.aspx).  
  
##  <a name="a-namegetshowcommenttagsa--chtmleditctrlbasegetshowcommenttags"></a><a name="getshowcommenttags"></a>CHtmlEditCtrlBase::GetShowCommentTags  
 Recupera si el control WebBrowser muestra un glifo para etiquetas de comentario.  
  
```  
HRESULT GetShowCommentTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra un glifo para etiquetas de comentario, false si no lo está.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWCOMMENTTAGS identificador de comando](https://msdn.microsoft.com/library/aa769950.aspx).  
  
##  <a name="a-namegetshowmisctagsa--chtmleditctrlbasegetshowmisctags"></a><a name="getshowmisctags"></a>CHtmlEditCtrlBase::GetShowMiscTags  
 Recupera si el control WebBrowser muestra todas las etiquetas que se muestran en Microsoft Internet Explorer 4.0.  
  
```  
HRESULT GetShowMiscTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra todas las etiquetas que se muestran en Microsoft Internet Explorer 4.0, false si no es así.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWMISCTAGS identificador de comando](https://msdn.microsoft.com/library/aa769952.aspx).  
  
##  <a name="a-namegetshowscripttagsa--chtmleditctrlbasegetshowscripttags"></a><a name="getshowscripttags"></a>CHtmlEditCtrlBase::GetShowScriptTags  
 Recupera si el control WebBrowser muestra un glifo para todas las etiquetas de script.  
  
```  
HRESULT GetShowScriptTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra un glifo para todas las etiquetas de script, false si no es así.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWSCRIPTTAGS identificador de comando](https://msdn.microsoft.com/library/aa769953.aspx).  
  
##  <a name="a-namegetshowstyletagsa--chtmleditctrlbasegetshowstyletags"></a><a name="getshowstyletags"></a>CHtmlEditCtrlBase::GetShowStyleTags  
 Recupera si el control WebBrowser muestra un glifo para todas las etiquetas de estilo.  
  
```  
HRESULT GetShowStyleTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra un glifo para todas las etiquetas de estilo, false si no lo  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWSTYLETAGS identificador de comando](https://msdn.microsoft.com/library/aa769954.aspx).  
  
##  <a name="a-namegetshowunknowntagsa--chtmleditctrlbasegetshowunknowntags"></a><a name="getshowunknowntags"></a>CHtmlEditCtrlBase::GetShowUnknownTags  
 Recupera si el control WebBrowser muestra un glifo para todas las etiquetas desconocidos.  
  
```  
HRESULT GetShowUnknownTags(bool& bCurValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bCurValue`  
 True si el control WebBrowser muestra un glifo para todas las etiquetas desconocidos, false si no es así.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IDM_SHOWUNKNOWNTAGS identificador de comando](https://msdn.microsoft.com/library/aa769955.aspx).  
  
##  <a name="a-namehorizontallinea--chtmleditctrlbasehorizontalline"></a><a name="horizontalline"></a>CHtmlEditCtrlBase::HorizontalLine  
 Sobrescribe una línea horizontal en la selección actual.  
  
```  
HRESULT HorizontalLine(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *NID*  
 El identificador de la línea horizontal.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_HORIZONTALLINE identificador de comando](https://msdn.microsoft.com/library/aa769968.aspx) para el control WebBrowser.  
  
##  <a name="a-namehyperlinka--chtmleditctrlbasehyperlink"></a><a name="hyperlink"></a>CHtmlEditCtrlBase::HyperLink  
 Inserta un hipervínculo en la selección actual.  
  
```  
HRESULT HyperLink(LPCTSTR szUrl = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szUrl`  
 La dirección URL del hipervínculo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_HYPERLINK identificador de comando](https://msdn.microsoft.com/library/aa769874.aspx) para el control WebBrowser.  
  
##  <a name="a-nameie50pastea--chtmleditctrlbaseie50paste"></a><a name="ie50paste"></a>CHtmlEditCtrlBase::IE50Paste  
 Realiza una operación de pegar es compatible con Internet Explorer 5.  
  
```  
HRESULT IE50Paste(LPCTSTR szData) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szData`  
 Cadena que se va a pegar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_IE50_PASTE identificador de comando](https://msdn.microsoft.com/library/aa769922.aspx) para el control WebBrowser.  
  
##  <a name="a-nameiframea--chtmleditctrlbaseiframe"></a><a name="iframe"></a>CHtmlEditCtrlBase::Iframe  
 Sobrescribe un marco en la selección actual.  
  
```  
HRESULT Iframe(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del marco flotante.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_IFRAME identificador de comando](https://msdn.microsoft.com/library/aa769969.aspx) para el control WebBrowser.  
  
##  <a name="a-nameimagea--chtmleditctrlbaseimage"></a><a name="image"></a>CHtmlEditCtrlBase::Image  
 Sobrescribe una imagen en la selección actual.  
  
```  
HRESULT Image(LPCTSTR szUrl = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szUrl`  
 La ruta de acceso y el nombre de la imagen que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_IMAGE identificador de comando](https://msdn.microsoft.com/library/aa769970.aspx) para el control WebBrowser.  
  
##  <a name="a-nameindenta--chtmleditctrlbaseindent"></a><a name="indent"></a>CHtmlEditCtrlBase::Indent  
 Aumenta la sangría del texto seleccionado en el incremento de una sangría.  
  
```  
HRESULT Indent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INDENT identificador de comando](https://msdn.microsoft.com/library/aa769963.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsfieldseta--chtmleditctrlbaseinsfieldset"></a><a name="insfieldset"></a>CHtmlEditCtrlBase::InsFieldSet  
 Sobrescribe un cuadro en la selección actual.  
  
```  
HRESULT InsFieldSet(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador de la casilla.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSFIELDSET identificador de comando](https://msdn.microsoft.com/library/aa769967.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsinputbuttona--chtmleditctrlbaseinsinputbutton"></a><a name="insinputbutton"></a>CHtmlEditCtrlBase::InsInputButton  
 Sobrescribe un control de botón en la selección actual.  
  
```  
HRESULT InsInputButton(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del control de botón.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSINPUTBUTTON identificador de comando](https://msdn.microsoft.com/library/aa769971.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsinputhiddena--chtmleditctrlbaseinsinputhidden"></a><a name="insinputhidden"></a>CHtmlEditCtrlBase::InsInputHidden  
 Inserta un control oculto en la selección actual.  
  
```  
HRESULT InsInputHidden(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el control oculto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSINPUTHIDDEN identificador de comando](https://msdn.microsoft.com/library/aa769974.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsinputimagea--chtmleditctrlbaseinsinputimage"></a><a name="insinputimage"></a>CHtmlEditCtrlBase::InsInputImage  
 Sobrescribe un control de imagen en la selección actual.  
  
```  
HRESULT InsInputImage(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el control de imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSINPUTIMAGE identificador de comando](https://msdn.microsoft.com/library/aa769975.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsinputpassworda--chtmleditctrlbaseinsinputpassword"></a><a name="insinputpassword"></a>CHtmlEditCtrlBase::InsInputPassword  
 Sobrescribe un control de contraseña en la selección actual.  
  
```  
HRESULT InsInputPassword(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el control de contraseña.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSINPUTPASSWORD identificador de comando](https://msdn.microsoft.com/library/aa769976.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsinputreseta--chtmleditctrlbaseinsinputreset"></a><a name="insinputreset"></a>CHtmlEditCtrlBase::InsInputReset  
 Sobrescribe un control de restablecimiento de la selección actual.  
  
```  
HRESULT InsInputReset(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el control de restablecimiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSINPUTRESET identificador de comando](https://msdn.microsoft.com/library/aa769978.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsinputsubmita--chtmleditctrlbaseinsinputsubmit"></a><a name="insinputsubmit"></a>CHtmlEditCtrlBase::InsInputSubmit  
 Sobrescribe un control enviar en la selección actual.  
  
```  
HRESULT InsInputSubmit(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el control de envío.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSINPUTSUBMIT identificador de comando](https://msdn.microsoft.com/library/aa769979.aspx) para el control WebBrowser.  
  
##  <a name="a-nameinsinputuploada--chtmleditctrlbaseinsinputupload"></a><a name="insinputupload"></a>CHtmlEditCtrlBase::InsInputUpload  
 Sobrescribe un control de carga de archivos en la selección actual.  
  
```  
HRESULT InsInputUpload(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el control de carga de archivos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_INSINPUTUPLOAD identificador de comando](https://msdn.microsoft.com/library/aa769973.aspx) para el control WebBrowser.  
  
##  <a name="a-nameis1delementa--chtmleditctrlbaseis1delement"></a><a name="is1delement"></a>CHtmlEditCtrlBase::Is1DElement  
 Determina si un elemento se coloca estáticamente.  
  
```  
HRESULT Is1DElement(bool& bValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bValue`  
 True si el elemento está colocado de forma estática.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_1D_ELEMENT identificador de comando](https://msdn.microsoft.com/library/aa769885.aspx) para el control WebBrowser.  
  
##  <a name="a-nameis2delementa--chtmleditctrlbaseis2delement"></a><a name="is2delement"></a>CHtmlEditCtrlBase::Is2DElement  
 Determina si un elemento se coloca absolutamente.  
  
```  
HRESULT Is2DElement(bool& bValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bValue`  
 True si el elemento está colocado de forma absoluta.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_2D_ELEMENT identificador de comando](https://msdn.microsoft.com/library/aa769886.aspx) para el control WebBrowser.  
  
##  <a name="a-nameitalica--chtmleditctrlbaseitalic"></a><a name="italic"></a>CHtmlEditCtrlBase::Italic  
 Alterna la selección actual entre cursiva y algunos.  
  
```  
HRESULT Italic() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_ITALIC identificador de comando](https://msdn.microsoft.com/library/aa769988.aspx) para el control WebBrowser.  
  
##  <a name="a-namejustifycentera--chtmleditctrlbasejustifycenter"></a><a name="justifycenter"></a>CHtmlEditCtrlBase::JustifyCenter  
 Centra el bloque del formato en que se encuentra la selección actual.  
  
```  
HRESULT JustifyCenter() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_JUSTIFYCENTER identificador de comando](https://msdn.microsoft.com/library/aa769989.aspx) para el control WebBrowser.  
  
##  <a name="a-namejustifylefta--chtmleditctrlbasejustifyleft"></a><a name="justifyleft"></a>CHtmlEditCtrlBase::JustifyLeft  
 Justifica a la izquierda el bloque del formato en que se encuentra la selección actual.  
  
```  
HRESULT JustifyLeft() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_JUSTIFYLEFT identificador de comando](https://msdn.microsoft.com/library/aa770011.aspx) para el control WebBrowser.  
  
##  <a name="a-namejustifyrighta--chtmleditctrlbasejustifyright"></a><a name="justifyright"></a>CHtmlEditCtrlBase::JustifyRight  
 Justifica a la derecha del bloque del formato en que se encuentra la selección actual.  
  
```  
HRESULT JustifyRight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_JUSTIFYRIGHT identificador de comando](https://msdn.microsoft.com/library/aa770013.aspx) para el control WebBrowser.  
  
##  <a name="a-namelistboxa--chtmleditctrlbaselistbox"></a><a name="listbox"></a>CHtmlEditCtrlBase::ListBox  
 Sobrescribe un control de selección de cuadro de lista en la selección actual.  
  
```  
HRESULT ListBox(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el control de cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_LISTBOX identificador de comando](https://msdn.microsoft.com/library/aa769985.aspx) para el control WebBrowser.  
  
##  <a name="a-namemarqueea--chtmleditctrlbasemarquee"></a><a name="marquee"></a>CHtmlEditCtrlBase::Marquee  
 Sobrescribe un recuadro vacío en la selección actual.  
  
```  
HRESULT Marquee(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador de la marquesina.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_MARQUEE identificador de comando](https://msdn.microsoft.com/library/aa769981.aspx) para el control WebBrowser.  
  
##  <a name="a-namenewdocumenta--chtmleditctrlbasenewdocument"></a><a name="newdocument"></a>CHtmlEditCtrlBase::NewDocument  
 Crea un nuevo documento.  
  
```  
HRESULT NewDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-nameorderlista--chtmleditctrlbaseorderlist"></a><a name="orderlist"></a>CHtmlEditCtrlBase::OrderList  
 Alterna la selección actual entre una lista ordenada y un bloque de formato normal.  
  
```  
HRESULT OrderList(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador de la lista ordenada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_ORDERLIST identificador de comando](https://msdn.microsoft.com/library/aa769982.aspx) para el control WebBrowser.  
  
##  <a name="a-nameoutdenta--chtmleditctrlbaseoutdent"></a><a name="outdent"></a>CHtmlEditCtrlBase::Outdent  
 Disminuye en un incremento la sangría del bloque de formato en que se encuentra la selección actual.  
  
```  
HRESULT Outdent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_OUTDENT identificador de comando](https://msdn.microsoft.com/library/aa770015.aspx) para el control WebBrowser.  
  
##  <a name="a-nameparagrapha--chtmleditctrlbaseparagraph"></a><a name="paragraph"></a>CHtmlEditCtrlBase::Paragraph  
 Sobrescribe un salto de línea en la selección actual.  
  
```  
HRESULT Paragraph(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador para el párrafo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_PARAGRAPH identificador de comando](https://msdn.microsoft.com/library/aa769983.aspx) para el control WebBrowser.  
  
##  <a name="a-namepastea--chtmleditctrlbasepaste"></a><a name="paste"></a>CHtmlEditCtrlBase::Paste  
 Sobrescribe el contenido del Portapapeles en la selección actual.  
  
```  
HRESULT Paste() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_PASTE identificador de comando](https://msdn.microsoft.com/library/aa770017.aspx) para el control WebBrowser.  
  
##  <a name="a-nameprintdocumenta--chtmleditctrlbaseprintdocument"></a><a name="printdocument"></a>CHtmlEditCtrlBase::PrintDocument  
 Imprime el documento actual.  
  
```  
HRESULT PrintDocument() const;  
HRESULT PrintDocument(LPCTSTR szPrintTemplate) const;  
HRESULT PrintDocument(bool bShowPrintDialog) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szPrintTemplate`  
 Ruta de acceso a una plantilla de impresión; Si no se especifica ninguno, se usa la plantilla de impresión predeterminada.  
  
 *bShowPrintDialog*  
 Si es true, muestra el cuadro de diálogo Imprimir.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_PRINT identificador de comando](https://msdn.microsoft.com/library/aa769937.aspx) para el control WebBrowser.  
  
##  <a name="a-nameprintpreviewa--chtmleditctrlbaseprintpreview"></a><a name="printpreview"></a>CHtmlEditCtrlBase::PrintPreview  
 Abre la ventana de vista previa de impresión del documento actual utilizando la plantilla predeterminada de la vista previa de impresión o una plantilla personalizada.  
  
```  
HRESULT PrintPreview() const;  
HRESULT PrintPreview(LPCTSTR szPrintTemplate) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szPrintTemplate`  
 Ruta de acceso a una plantilla de impresión.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_PRINTPREVIEW identificador de comando](https://msdn.microsoft.com/library/aa769938.aspx) para el control WebBrowser.  
  
##  <a name="a-namequerystatusa--chtmleditctrlbasequerystatus"></a><a name="querystatus"></a>CHtmlEditCtrlBase::QueryStatus  
 Llame a este método para consultar el estado de comandos.  
  
```  
long QueryStatus(long cmdID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 Identificador del comando. Identificadores de comando se toman de la `CGID_MSHTML`del grupo de comandos. Estos comandos se definen en Mshtmcid.h. También puede encontrar la lista en línea en [identificadores de comandos de MSHTML](http://go.microsoft.com/fwlink/linkid=149220).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un [OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237) que indica el estado de `cmdID`, o 0 en caso de error.  
  
##  <a name="a-nameradiobuttona--chtmleditctrlbaseradiobutton"></a><a name="radiobutton"></a>CHtmlEditCtrlBase::RadioButton  
 Sobrescribe un control de radio en la selección actual.  
  
```  
HRESULT RadioButton(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del botón de radio.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_RADIOBUTTON identificador de comando](https://msdn.microsoft.com/library/aa769977.aspx) para el control WebBrowser.  
  
##  <a name="a-namerefreshdocumenta--chtmleditctrlbaserefreshdocument"></a><a name="refreshdocument"></a>CHtmlEditCtrlBase::RefreshDocument  
 Actualiza el documento actual.  
  
```  
HRESULT RefreshDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_REFRESH identificador de comando](https://msdn.microsoft.com/library/aa770020.aspx) para el control WebBrowser.  
  
##  <a name="a-nameremoveformata--chtmleditctrlbaseremoveformat"></a><a name="removeformat"></a>CHtmlEditCtrlBase::RemoveFormat  
 Quita las etiquetas de formato de la selección actual.  
  
```  
HRESULT RemoveFormat() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_REMOVEFORMAT identificador de comando](https://msdn.microsoft.com/library/aa770021.aspx) para el control WebBrowser.  
  
##  <a name="a-namesaveasa--chtmleditctrlbasesaveas"></a><a name="saveas"></a>CHtmlEditCtrlBase::SaveAs  
 Guarda la página Web actual en un archivo.  
  
```  
HRESULT SaveAs(LPCTSTR szPath = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szPath`  
 La ruta de acceso y el nombre que se va a guardar la página Web.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_SAVEAS el Id. de comando](https://msdn.microsoft.com/library/aa770024.aspx) para el control WebBrowser.  
  
##  <a name="a-nameselectalla--chtmleditctrlbaseselectall"></a><a name="selectall"></a>CHtmlEditCtrlBase::SelectAll  
 Selecciona todo el documento.  
  
```  
HRESULT SelectAll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_SELECTALL identificador de comando](https://msdn.microsoft.com/library/aa770025.aspx) para el control WebBrowser.  
  
##  <a name="a-nameset2dpositiona--chtmleditctrlbaseset2dposition"></a><a name="set2dposition"></a>CHtmlEditCtrlBase::Set2DPosition  
 Permite mover arrastrando elementos con posición absoluta.  
  
```  
HRESULT Set2DPosition(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, se pueden mover elementos con posición absoluta arrastrando.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_2D_POSITION identificador de comando](https://msdn.microsoft.com/library/aa769887.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetabsolutepositiona--chtmleditctrlbasesetabsoluteposition"></a><a name="setabsoluteposition"></a>CHtmlEditCtrlBase::SetAbsolutePosition  
 Establece la propiedad de posición de un elemento "absoluto" o "estático".  
  
```  
HRESULT SetAbsolutePosition(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, la propiedad de posición del elemento es "absoluta"; Si es false, que es "estático".  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_ABSOLUTE_POSITION identificador de comando](https://msdn.microsoft.com/library/aa769889.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetatomicselectiona--chtmleditctrlbasesetatomicselection"></a><a name="setatomicselection"></a>CHtmlEditCtrlBase::SetAtomicSelection  
 Establecer el modo de selección atómica.  
  
```  
HRESULT SetAtomicSelection(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, cualquier elemento que tenga un atributo ATOMICSELECTION establecido en TRUE se puede seleccionar sólo como una unidad.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_ATOMICSELECTION identificador de comando](https://msdn.microsoft.com/library/aa769892.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetautourldetectmodea--chtmleditctrlbasesetautourldetectmode"></a><a name="setautourldetectmode"></a>CHtmlEditCtrlBase::SetAutoURLDetectMode  
 Activa la detección automática de dirección URL y desactiva.  
  
```  
HRESULT SetAutoURLDetectMode(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, se habilita la detección automática de dirección URL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_AUTOURLDETECT_MODE identificador de comando](https://msdn.microsoft.com/library/aa769893.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetbackcolora--chtmleditctrlbasesetbackcolor"></a><a name="setbackcolor"></a>CHtmlEditCtrlBase::SetBackColor  
 Establece el color de fondo de la selección actual.  
  
```  
HRESULT SetBackColor(int nColor) const;  
HRESULT SetBackColor(LPCTSTR szColor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nColor`  
 El color. Consulte `pvaIn` en [IDM_BACKCOLOR identificador de comando](https://msdn.microsoft.com/library/aa769858.aspx).  
  
 `szColor`  
 El color. Consulte `pvaIn` en [IDM_BACKCOLOR identificador de comando](https://msdn.microsoft.com/library/aa769858.aspx).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_BACKCOLOR_ identificador de comando](https://msdn.microsoft.com/library/aa769858.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetblockformata--chtmleditctrlbasesetblockformat"></a><a name="setblockformat"></a>CHtmlEditCtrlBase::SetBlockFormat  
 Establece la etiqueta de formato de bloque actual.  
  
```  
HRESULT SetBlockFormat(LPCTSTR szFormat) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szFormat`  
 La etiqueta de formato.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_BLOCKFMT_command ID](https://msdn.microsoft.com/library/aa769883.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetbookmarka--chtmleditctrlbasesetbookmark"></a><a name="setbookmark"></a>CHtmlEditCtrlBase::SetBookMark  
 Crea un delimitador de marcador para el punto de inserción o la selección actual.  
  
```  
HRESULT SetBookMark(LPCTSTR szAnchorName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *szAnchorName*  
 El nombre del delimitador.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_BOOKMARK identificador de comando](https://msdn.microsoft.com/library/aa769873.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetcsseditinglevela--chtmleditctrlbasesetcsseditinglevel"></a><a name="setcsseditinglevel"></a>CHtmlEditCtrlBase::SetCSSEditingLevel  
 Selecciona el nivel CSS (partir de CSS1 o CSS2) el editor admitirá, si existe.  
  
```  
HRESULT SetCSSEditingLevel(short nLevel) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nLevel`  
 El nivel de CSS. Pase 0 si no desea compatibilidad con CSS.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_CSSEDITING_LEVEL identificador de comando](https://msdn.microsoft.com/library/aa769903.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetdefaultcomposesettingsa--chtmleditctrlbasesetdefaultcomposesettings"></a><a name="setdefaultcomposesettings"></a>CHtmlEditCtrlBase::SetDefaultComposeSettings  
 Configuración de redacción de este método para establecer el valor predeterminado de llamada.  
  
```  
HRESULT SetDefaultComposeSettings(
    LPCSTR szFontName = NULL,  
    unsigned short nFontSize = 3,  
    COLORREF crFontColor = 0xFF000000,  
    COLORREF crFontBgColor = 0xFF000000,  
    bool bBold = false,  
    bool bItalic = false,  
    bool bUnderline = false) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *szFontName*  
 El nombre de la fuente.  
  
 *nFontSize*  
 El tamaño de fuente.  
  
 *crFontColor*  
 El color de fuente.  
  
 *crFontBgColor*  
 El color de fondo de la fuente.  
  
 *bnegrita*  
 Pasa true para el texto en negrita.  
  
 `bItalic`  
 Pasa true para el texto en cursiva.  
  
 `bUnderline`  
 Pasa true para el texto subrayado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_COMPOSESETTINGS el Id. de comando](https://msdn.microsoft.com/library/aa769901.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetdesignmodea--chtmleditctrlbasesetdesignmode"></a><a name="setdesignmode"></a>CHtmlEditCtrlBase::SetDesignMode  
 Establecer el modo de diseño.  
  
```  
BOOL SetDesignMode(BOOL bMode) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bMode`  
 Si es true, activa el modo de diseño.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="a-namesetdisableeditfocusuia--chtmleditctrlbasesetdisableeditfocusui"></a><a name="setdisableeditfocusui"></a>CHtmlEditCtrlBase::SetDisableEditFocusUI  
 Deshabilita el borde sombreado y alrededor de un elemento que tiene el foco de la edición.  
  
```  
HRESULT SetDisableEditFocusUI(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, deshabilita el borde sombreado y controladores alrededor de un elemento seleccionable del sitio cuando el elemento "Editar foco" en modo de diseño; es decir, cuando el texto o el contenido del elemento se puede editar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM_DISABLE_EDITFOCUS_UI identificador de comando](https://msdn.microsoft.com/library/aa769905.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetdocumenthtmla--chtmleditctrlbasesetdocumenthtml"></a><a name="setdocumenthtml"></a>CHtmlEditCtrlBase::SetDocumentHTML  
 Establece el código HTML del documento actual.  
  
```  
HRESULT SetDocumentHTML(LPCTSTR szHTML) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szHTML`  
 El código HTML.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namesetfontfacea--chtmleditctrlbasesetfontface"></a><a name="setfontface"></a>CHtmlEditCtrlBase::SetFontFace  
 Establece la fuente para la selección actual.  
  
```  
HRESULT SetFontFace(LPCTSTR szFace) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szFace`  
 El nombre de la fuente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM FONTNAME](https://msdn.microsoft.com/library/aa769880.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetfontsizea--chtmleditctrlbasesetfontsize"></a><a name="setfontsize"></a>CHtmlEditCtrlBase::SetFontSize  
 Establece el tamaño de fuente para la selección actual.  
  
```  
HRESULT SetFontSize(unsigned short size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 El tamaño de fuente HTML (1-7). Un valor de 0, Establece el tamaño de fuente en 1.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM FONTSIZE](https://msdn.microsoft.com/library/aa769881.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetforecolora--chtmleditctrlbasesetforecolor"></a><a name="setforecolor"></a>CHtmlEditCtrlBase::SetForeColor  
 Establece el color de primer plano (texto) de la selección actual.  
  
```  
HRESULT SetForeColor(LPCTSTR szColor) const;  
HRESULT SetForeColor(int nColor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szColor`  
 El color.  
  
 `nColor`  
 El color.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM FORECOLOR](https://msdn.microsoft.com/library/aa769882.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetie5pastemodea--chtmleditctrlbasesetie5pastemode"></a><a name="setie5pastemode"></a>CHtmlEditCtrlBase::SetIE5PasteMode  
 Establece la operación de pegar para ser compatible con Microsoft Internet Explorer 5.  
  
```  
HRESULT SetIE5PasteMode(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, todas las operaciones de pegar son compatibles con Internet Explorer 5; Si es false, las operaciones de pegar son compatibles con Internet Explorer 5.5.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM IE50_PASTE_MODE](https://msdn.microsoft.com/library/aa769923.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetliveresizea--chtmleditctrlbasesetliveresize"></a><a name="setliveresize"></a>CHtmlEditCtrlBase::SetLiveResize  
 Hace que el control WebBrowser actualizar la apariencia de un elemento continuamente durante una operación de movimiento o cambio de tamaño, en lugar de actualizar solamente al final del movimiento o cambiar el tamaño.  
  
```  
HRESULT SetLiveResize(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, hace que el control WebBrowser actualizar la apariencia de un elemento continuamente durante una operación de cambio de tamaño o mover; Si es false, actualiza solo al final del movimiento o cambio de tamaño.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM LIVERESIZE](https://msdn.microsoft.com/library/aa769928.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetmultiselecta--chtmleditctrlbasesetmultiselect"></a><a name="setmultiselect"></a>CHtmlEditCtrlBase::SetMultiSelect  
 Permite la selección múltiple.  
  
```  
HRESULT SetMultiSelect(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, permite la selección de más de un elemento seleccionable para el sitio a la vez cuando el usuario mantiene presionada las teclas MAYÚS o CTRL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM MULTIPLESELECTION](https://msdn.microsoft.com/library/aa769929.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetoverridecursora--chtmleditctrlbasesetoverridecursor"></a><a name="setoverridecursor"></a>CHtmlEditCtrlBase::SetOverrideCursor  
 Comandos WebBrowser nunca para cambiar el puntero del mouse.  
  
```  
HRESULT SetOverrideCursor(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, el control WebBrowser no cambiará el puntero del mouse.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM OVERRIDE_CURSOR](https://msdn.microsoft.com/library/aa769932.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetoverwritemodea--chtmleditctrlbasesetoverwritemode"></a><a name="setoverwritemode"></a>CHtmlEditCtrlBase::SetOverwriteMode  
 Activa o desactiva el modo de entrada de texto entre insertar y sobrescribir.  
  
```  
HRESULT SetOverwriteMode(bool bMode) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bMode`  
 Si es true, se sobrescribe el modo de entrada de texto; Si es false, el modo de entrada de texto es insert.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM SOBRESCRIBIR el identificador de comando](https://msdn.microsoft.com/library/aa770016.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetrespectvisindesigna--chtmleditctrlbasesetrespectvisindesign"></a><a name="setrespectvisindesign"></a>CHtmlEditCtrlBase::SetRespectVisInDesign  
 Oculta los elementos invisibles en modo de diseño.  
  
```  
HRESULT SetRespectVisInDesign(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, los elementos que tienen una visibilidad establecido en "hidden" o mostrar la propiedad establecida en "none" no se muestra en modo de diseño y modo de exploración; Si es false, los elementos se mostrarán sólo en modo de exploración.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM RESPECTVISIBILITY_INDESIGN](https://msdn.microsoft.com/library/aa770023.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowalignedsitetagsa--chtmleditctrlbasesetshowalignedsitetags"></a><a name="setshowalignedsitetags"></a>CHtmlEditCtrlBase::SetShowAlignedSiteTags  
 Muestra un glifo para todos los elementos que tienen un **styleFloat** propiedad.  
  
```  
HRESULT SetShowAlignedSiteTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, se muestra un glifo para todos los elementos que tienen un **styleFloat** propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWALIGNEDSITETAGS](https://msdn.microsoft.com/library/aa769947.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowalltagsa--chtmleditctrlbasesetshowalltags"></a><a name="setshowalltags"></a>CHtmlEditCtrlBase::SetShowAllTags  
 Muestra los glifos para mostrar la ubicación de todas las etiquetas de un documento.  
  
```  
HRESULT SetShowAllTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra los glifos para mostrar la ubicación de todas las etiquetas de un documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWALLTAGS](https://msdn.microsoft.com/library/aa769948.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowareatagsa--chtmleditctrlbasesetshowareatags"></a><a name="setshowareatags"></a>CHtmlEditCtrlBase::SetShowAreaTags  
 Muestra un glifo para todas las etiquetas de área.  
  
```  
HRESULT SetShowAreaTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra un glifo para todas las etiquetas de área.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWAREATAGS](https://msdn.microsoft.com/library/aa769949.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowbrtagsa--chtmleditctrlbasesetshowbrtags"></a><a name="setshowbrtags"></a>CHtmlEditCtrlBase::SetShowBRTags  
 Muestra un glifo para todas las etiquetas br.  
  
```  
HRESULT SetShowBRTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra un glifo para todas las etiquetas br.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWWBRTAGS](https://msdn.microsoft.com/library/aa769956.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowcommenttagsa--chtmleditctrlbasesetshowcommenttags"></a><a name="setshowcommenttags"></a>CHtmlEditCtrlBase::SetShowCommentTags  
 Muestra un glifo para todas las etiquetas de comentario.  
  
```  
HRESULT SetShowCommentTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra un glifo para todas las etiquetas de comentario.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWCOMMENTTAGS](https://msdn.microsoft.com/library/aa769950.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowmisctagsa--chtmleditctrlbasesetshowmisctags"></a><a name="setshowmisctags"></a>CHtmlEditCtrlBase::SetShowMiscTags  
 Muestra todas las etiquetas que se muestran en Microsoft Internet Explorer 4.0.  
  
```  
HRESULT SetShowMiscTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra todas las etiquetas que se muestran en Microsoft Internet Explorer 4.0.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWMISCTAGS](https://msdn.microsoft.com/library/aa769952.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowscripttagsa--chtmleditctrlbasesetshowscripttags"></a><a name="setshowscripttags"></a>CHtmlEditCtrlBase::SetShowScriptTags  
 Muestra un glifo para todas las etiquetas de script.  
  
```  
HRESULT SetShowScriptTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra un glifo para todas las etiquetas de script.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWSCRIPTTAGS](https://msdn.microsoft.com/library/aa769953.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowstyletagsa--chtmleditctrlbasesetshowstyletags"></a><a name="setshowstyletags"></a>CHtmlEditCtrlBase::SetShowStyleTags  
 Muestra un glifo para todas las etiquetas de estilo.  
  
```  
HRESULT SetShowStyleTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra un glifo para todas las etiquetas de estilo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWSTYLETAGS](https://msdn.microsoft.com/library/aa769954.aspx) para el control WebBrowser.  
  
##  <a name="a-namesetshowunknowntagsa--chtmleditctrlbasesetshowunknowntags"></a><a name="setshowunknowntags"></a>CHtmlEditCtrlBase::SetShowUnknownTags  
 Muestra un glifo para todas las etiquetas desconocidos.  
  
```  
HRESULT SetShowUnknownTags(bool bNewValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `bNewValue`  
 Si es true, muestra un glifo para todas las etiquetas desconocidos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM SHOWUNKNOWNTAGS](https://msdn.microsoft.com/library/aa769955.aspx) para el control WebBrowser.  
  
##  <a name="a-nametextareaa--chtmleditctrlbasetextarea"></a><a name="textarea"></a>CHtmlEditCtrlBase::TextArea  
 Sobrescribe un control de entrada de texto de varias líneas en la selección actual.  
  
```  
HRESULT TextArea(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del control de entrada de texto multilínea.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM TEXTAREA](https://msdn.microsoft.com/library/aa769986.aspx) para el control WebBrowser.  
  
##  <a name="a-nametextboxa--chtmleditctrlbasetextbox"></a><a name="textbox"></a>CHtmlEditCtrlBase::TextBox  
 Sobrescribe un control de texto en la selección actual.  
  
```  
HRESULT TextBox(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador del control de texto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM TEXTBOX](https://msdn.microsoft.com/library/aa769980.aspx) para el control WebBrowser.  
  
##  <a name="a-nameunbookmarka--chtmleditctrlbaseunbookmark"></a><a name="unbookmark"></a>CHtmlEditCtrlBase::UnBookmark  
 Quita los marcadores de la selección actual.  
  
```  
HRESULT UnBookmark() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [UNBOOKMARK IDM Id. de comando](https://msdn.microsoft.com/library/aa770034.aspx) para el control WebBrowser.  
  
##  <a name="a-nameunderlinea--chtmleditctrlbaseunderline"></a><a name="underline"></a>CHtmlEditCtrlBase::Underline  
 Alterna la selección actual entre subrayado y no subrayado.  
  
```  
HRESULT Underline() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM SUBRAYAR el identificador de comando](https://msdn.microsoft.com/library/aa770035.aspx) para el control WebBrowser.  
  
##  <a name="a-nameunlinka--chtmleditctrlbaseunlink"></a><a name="unlink"></a>CHtmlEditCtrlBase::Unlink  
 Quita cualquier hipervínculo de la selección actual.  
  
```  
HRESULT Unlink() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [IDM DESVINCULAR el identificador de comando](https://msdn.microsoft.com/library/aa770037.aspx) para el control WebBrowser.  
  
##  <a name="a-nameunorderlista--chtmleditctrlbaseunorderlist"></a><a name="unorderlist"></a>CHtmlEditCtrlBase::UnorderList  
 Alterna la selección actual entre una lista ordenada y un bloque de formato normal.  
  
```  
HRESULT UnorderList(LPCTSTR szId = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `szId`  
 El identificador de la lista sin ordenar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [identificador de comando de IDM UNORDERLIST](https://msdn.microsoft.com/library/aa769987.aspx) para el control WebBrowser.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Ejemplo HTMLEdit](../../visual-cpp-samples.md)


