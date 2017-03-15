---
title: "Formato CString y presentación del cuadro de mensaje | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.strings
dev_langs:
- C++
helpviewer_keywords:
- CString objects, formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
caps.latest.revision: 14
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 48fc79f74bda10e43807d57fbcd7ed85fbb5d78b
ms.lasthandoff: 02/24/2017

---
# <a name="cstring-formatting-and-message-box-display"></a>Formato y presentación del cuadro de mensaje CString
Se proporciona una serie de funciones para dar formato y analizar `CString` objetos. Puede utilizar estas funciones siempre tiene que manipular `CString` objetos, pero son especialmente útiles para dar formato a cadenas que aparecerán en el cuadro de mensaje de texto.  
  
 Este grupo de funciones también incluye una rutina global para mostrar un cuadro de mensaje.  
  
### <a name="cstring-functions"></a>Funciones de CString  
  
|||  
|-|-|  
|[AfxExtractSubString](#afxextractsubstring)|Extrae subcadenas separados por un carácter de una cadena de origen determinado.|  
|[AfxFormatString1](#afxformatstring1)|Sustituye una cadena determinada para los caracteres de formato "%1" en una cadena de contenido en la tabla de cadenas.|  
|[AfxFormatString2](#afxformatstring2)|Cadenas de sustitutos dos para el formato de caracteres "%1" y "%2" en una cadena de contenido en la tabla de cadenas.|  
|[AfxMessageBox](#afxmessagebox)|Muestra un cuadro de mensaje.|  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="a-nameafxextractsubstringa--afxextractsubstring"></a><a name="afxextractsubstring"></a>AfxExtractSubString  
 Esta función global puede utilizarse para extraer una subcadena de una cadena de origen determinado.  
  
```   
BOOL AFXAPI AfxExtractSubString (
    CString& rString,  
    LPCTSTR lpszFullString,  
    int iSubString,  
    TCHAR chSep  = '\n'); 
```  
  
### <a name="parameters"></a>Parámetros  
 *rString*  
 -   Hacer referencia a un [CString](../../atl-mfc-shared/using-cstring.md) objeto que recibirá una subcadena individual.  
  
 *lpszFullString*  
 -   Cadena que contiene el texto completo de la cadena se extraen.  
  
 *iSubString*  
 -   Índice de base cero de la subcadena que se va a extraer de *lpszFullString*.  
  
 *chSep*  
 -   Carácter de separador que se utiliza para delimitar las subcadenas.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la función extrae correctamente la subcadena en el índice proporcionado; de lo contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es útil para extraer varias subcadenas de una cadena de origen cuando un único carácter conocido separa cada subcadena. Esta función busca desde el principio de la `lpszFullString` parámetro cada vez que se llama.  
  
 Esta función devolverá FALSE si `lpszFullString` está establecido en **NULL** o la función llega al final de `lpszFullString` sin buscar `iSubString`+&1; apariciones del carácter separador especificado. El `rString` parámetro no se modificará su valor original si `lpszFullString` se estableció en **NULL**; en caso contrario, el `rString` parámetro se establece en la cadena vacía si no se pudo extraer la subcadena para el índice especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities Nº&48;](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="a-nameafxformatstring1a--afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1  
 Sustituye la cadena señalada por `lpsz1` para todas las instancias de los caracteres "%1" en el recurso de cadena de plantilla identificado por `nIDS`.  
  
```  
void  AfxFormatString1(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1); 
```  
  
### <a name="parameters"></a>Parámetros  
 `rString`  
 Una referencia a un `CString` objeto que contendrá la cadena resultante después de realiza la sustitución.  
  
 `nIDS`  
 El identificador de recurso de la cadena de plantilla en el que se realizará la sustitución.  
  
 `lpsz1`  
 Cadena que va a reemplazar el formato de caracteres "%1" en la cadena de plantilla.  
  
### <a name="remarks"></a>Comentarios  
 La cadena recién creada se almacena en `rString`. Por ejemplo, si la cadena de la tabla de cadenas es "Archivo no se encontró %1", y `lpsz1` es igual a "C:\MYFILE. TXT", a continuación, `rString` contendrá la cadena"archivo C:\MYFILE. TXT no encontrado". Esta función es útil para dar formato a las cadenas enviadas a otras ventanas y cuadros de mensaje.  
  
 Si los caracteres de formato "%1" aparecen en la cadena de más de una vez, se realizarán varias sustituciones.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#25;](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="a-nameafxformatstring2a--afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2  
 Sustituye la cadena señalada por `lpsz1` para todas las instancias de los caracteres "%1" y la cadena señalada por `lpsz2` para todas las instancias de los caracteres "%2", en el recurso de cadena de plantilla identificado por `nIDS`.  
  
```   
void AfxFormatString2(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1,  
    LPCTSTR lpsz2); 
```  
  
### <a name="parameters"></a>Parámetros  
 `rString`  
 Una referencia a la `CString` que contendrá la cadena resultante después de realiza la sustitución.  
  
 `nIDS`  
 Id. de tabla de cadena de la cadena de plantilla en el que se realizará la sustitución.  
  
 `lpsz1`  
 Cadena que va a reemplazar el formato de caracteres "%1" en la cadena de plantilla.  
  
 `lpsz2`  
 Cadena que va a reemplazar el formato de caracteres "%2" en la cadena de plantilla.  
  
### <a name="remarks"></a>Comentarios  
 La cadena recién creada se almacena en `rString`. Por ejemplo, si la cadena de la tabla de cadenas es "Archivo %1 no se encuentra en el directorio %2", `lpsz1` apunta a "MIARCHIVO. "TXT", y `lpsz2` apunta a "C:\MYDIR", a continuación, `rString` contendrá la cadena "archivo MYFILE. No se encuentra en el directorio C:\MYDIR "TXT"  
  
 Si el formato de caracteres "%1" o "%2" no aparece en la cadena de más de una vez, se realizarán varias sustituciones. No tiene que estar en orden numérico.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFC_Utilities #](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="a-nameafxmessageboxa--afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox  
 Muestra un cuadro de mensaje en la pantalla.  
  
```  
int AfxMessageBox(
    LPCTSTR lpszText,  
    UINT nType = MB_OK,  
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,  
    UINT nType = MB_OK,  
    UINT nIDHelp = (UINT) -1); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Apunta a un `CString` objeto o cadena terminada en null que contiene el mensaje que se mostrará en el cuadro de mensaje.  
  
 `nType`  
 El estilo del cuadro de mensaje. Aplicar cualquiera de los [estilos de cuadro de mensaje](../../mfc/reference/message-box-styles.md) al cuadro.  
  
 `nIDHelp`  
 El identificador de contexto de ayuda para el mensaje; 0 indica que se utilizará el contexto de Ayuda de la aplicación predeterminada.  
  
 `nIDPrompt`  
 Identificador único que se utiliza para hacer referencia a una cadena en la tabla de cadenas.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si no hay memoria suficiente para mostrar el cuadro de mensaje; de lo contrario, se devuelve uno de los siguientes valores:  
  
- **IDABORT** anular el botón se ha seleccionado.  
  
- **IDCANCEL** cancelar el botón se ha seleccionado.  
  
- **IDIGNORE** se ha seleccionado omitir el botón.  
  
- **IDNO** botón el No se ha seleccionado.  
  
- **IDOK** se selecciona Aceptar el botón.  
  
- **IDRETRY** intente de nuevo el botón se ha seleccionado.  
  
- **IDYES** sí el botón se ha seleccionado.  
  
 Si un cuadro de mensaje tiene un botón Cancelar, el **IDCANCEL** se devolverá el valor si se presiona la tecla ESC o si se selecciona el botón Cancelar. Si el cuadro de mensaje no tiene ningún botón Cancel, presionar la tecla ESC tiene ningún efecto.  
  
 Las funciones [AfxFormatString1](#afxformatstring1) y [AfxFormatString2](#afxformatstring2) puede ser útil para dar formato al texto que aparece en un cuadro de mensaje.  
  
### <a name="remarks"></a>Comentarios  
 La primera forma de esta sobrecarga función muestra una cadena de texto que señala `lpszText` en el cuadro de mensaje y utiliza `nIDHelp` para describir un contexto de ayuda. Para saltar a un tema de ayuda asociado cuando el usuario presiona la tecla de ayuda (normalmente F1), se utiliza el contexto de ayuda.  
  
 La segunda forma de la función usa el recurso de cadena con el identificador `nIDPrompt` para mostrar un mensaje en el cuadro de mensaje. La página de ayuda asociada se encuentra mediante el valor de `nIDHelp`. Si el valor predeterminado de `nIDHelp` se usa (â €"1), el identificador de recurso de cadena `nIDPrompt`, se utiliza para el contexto de ayuda. Para obtener más información acerca de cómo definir los contextos de ayuda, consulte [28 de nota técnica](../../mfc/tn028-context-sensitive-help-support.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#133;](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)

