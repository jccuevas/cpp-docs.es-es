---
title: Formato CString y presentación del cuadro de mensaje | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.strings
dev_langs:
- C++
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8074d84d739b59acfa0c6040bedf76f46b6ea9c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375046"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formato y presentación del cuadro de mensaje CString
Se proporciona una serie de funciones para dar formato y analizar `CString` objetos. Puede usar estas funciones siempre tiene que manipular `CString` objetos, pero son especialmente útiles para dar formato a cadenas que va a aparecer en el texto de cuadro de mensaje.  
  
 Este grupo de funciones también incluye una rutina global para mostrar un cuadro de mensaje.  
  
### <a name="cstring-functions"></a>Funciones de CString  
  
|||  
|-|-|  
|[AfxExtractSubString](#afxextractsubstring)|Extrae subcadenas separados por un único carácter de una cadena de origen especificado.|  
|[AfxFormatString1](#afxformatstring1)|Sustituye una cadena determinada para los caracteres de formato "%1" en una cadena de contenido en la tabla de cadenas.|  
|[AfxFormatString2](#afxformatstring2)|Cadenas de sustituye dos para el formato de caracteres "%1" y "%2" en una cadena de contenido en la tabla de cadenas.|  
|[AfxMessageBox](#afxmessagebox)|Muestra un cuadro de mensaje.|  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxextractsubstring"></a>  AfxExtractSubString  
 Esta función global puede utilizarse para extraer una subcadena de una cadena de origen especificado.  
  
```   
BOOL AFXAPI AfxExtractSubString (
    CString& rString,  
    LPCTSTR lpszFullString,  
    int iSubString,  
    TCHAR chSep  = '\n'); 
```  
  
### <a name="parameters"></a>Parámetros  
 *rString*  
 -   Referencia a un [CString](../../atl-mfc-shared/using-cstring.md) objeto que va a recibir una subcadena individual.  
  
 *lpszFullString*  
 -   Cadena que contiene el texto completo de la cadena se extraen.  
  
 *iSubString*  
 -   Índice de base cero de la subcadena que se va a extraer de *lpszFullString*.  
  
 *chSep*  
 -   Carácter de separador que se utiliza para delimitar subcadenas.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la función correctamente extrae la subcadena en el índice proporcionado; de lo contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es útil para extraer varias subcadenas de una cadena de origen cuando un único carácter conocido separa cada subcadena. Esta función busca desde el principio de la `lpszFullString` parámetro cada vez que se llama.  
  
 Esta función devuelve FALSE si el valor `lpszFullString` está establecido en **NULL** o la función llega al final del `lpszFullString` sin buscar `iSubString`+ 1 apariciones del carácter separador especificado. El `rString` parámetro no se modificarán respecto de su valor original si `lpszFullString` se estableció en **NULL**; en caso contrario, el `rString` parámetro se establece en la cadena vacía si no se pudo extraer la subcadena para el elemento especificado índice.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxformatstring1"></a>  AfxFormatString1  
 Sustituye la cadena que señala `lpsz1` para todas las instancias de los caracteres "%1" en el recurso de cadena de plantilla identificado por `nIDS`.  
  
```  
void  AfxFormatString1(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1); 
```  
  
### <a name="parameters"></a>Parámetros  
 `rString`  
 Una referencia a un `CString` objeto que va a contener la cadena resultante una vez realizada la sustitución.  
  
 `nIDS`  
 El identificador de recurso de la cadena de plantilla en el que se realizará la sustitución.  
  
 `lpsz1`  
 Cadena que va a reemplazar el formato de caracteres "%1" en la cadena de plantilla.  
  
### <a name="remarks"></a>Comentarios  
 La cadena recién creada se almacena en `rString`. Por ejemplo, si la cadena de la tabla de cadenas es "Archivo %1 no encontrado", y `lpsz1` es igual a "C:\MYFILE. "TXT", a continuación, `rString` contendrá la cadena "File C:\MYFILE. TXT no encontrado". Esta función es útil para dar formato a las cadenas enviadas a otras ventanas y cuadros de mensaje.  
  
 Si los caracteres de formato "%1" aparecen en la cadena de más de una vez, se realizarán varias sustituciones.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxformatstring2"></a>  AfxFormatString2  
 Sustituye la cadena que señala `lpsz1` para todas las instancias de los caracteres "%1" y la cadena que señala `lpsz2` para todas las instancias de los caracteres "%2", en el recurso de cadena de plantilla identificado por `nIDS`.  
  
```   
void AfxFormatString2(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1,  
    LPCTSTR lpsz2); 
```  
  
### <a name="parameters"></a>Parámetros  
 `rString`  
 Una referencia a la `CString` que contendrá la cadena resultante una vez realizada la sustitución.  
  
 `nIDS`  
 El identificador de la tabla de cadena de la cadena de plantilla en el que se realizará la sustitución.  
  
 `lpsz1`  
 Cadena que va a reemplazar el formato de caracteres "%1" en la cadena de plantilla.  
  
 `lpsz2`  
 Cadena que va a reemplazar el formato de caracteres "%2" en la cadena de plantilla.  
  
### <a name="remarks"></a>Comentarios  
 La cadena recién creada se almacena en `rString`. Por ejemplo, si la cadena de la tabla de cadenas es "Archivo %1 no se encuentra en el directorio %2", `lpsz1` apunta a "MIARCHIVO. "TXT", y `lpsz2` apunta a "C:\MYDIR", a continuación, `rString` contendrá la cadena "archivo MYFILE. No se encuentra en el directorio C:\MYDIR "TXT"  
  
 Si el formato de caracteres "%1" o "%2" no aparece en la cadena de más de una vez, se realizarán varias sustituciones. No tiene que estar en orden numérico.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxmessagebox"></a>  AfxMessageBox  
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
 El estilo del cuadro de mensaje. Aplicar cualquiera de los [estilos de cuadro de mensaje](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) al cuadro.  
  
 `nIDHelp`  
 El identificador de contexto de ayuda para el mensaje; 0 indica que se utilizará el contexto de Ayuda de la aplicación predeterminada.  
  
 `nIDPrompt`  
 Un identificador único usado para hacer referencia a una cadena en la tabla de cadenas.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si no hay suficiente memoria para mostrar el cuadro de mensaje; en caso contrario, se devuelve uno de los siguientes valores:  
  
- **IDABORT** anular el botón se ha seleccionado.  
  
- **IDCANCEL** cancelar el botón se ha seleccionado.  
  
- **IDIGNORE** omitir el botón se ha seleccionado.  
  
- **IDNO** botón el No se ha seleccionado.  
  
- **IDOK** Aceptar el botón se ha seleccionado.  
  
- **IDRETRY** intente de nuevo el botón se ha seleccionado.  
  
- **IDYES** sí el botón se ha seleccionado.  
  
 Si un cuadro de mensaje tiene un botón de cancelación, el **IDCANCEL** se devolverá el valor si se presiona la tecla ESC o si se selecciona el botón Cancelar. Si el cuadro de mensaje no tiene ningún botón Cancelar, presionar la tecla ESC tiene ningún efecto.  
  
 Las funciones [AfxFormatString1](#afxformatstring1) y [AfxFormatString2](#afxformatstring2) puede ser útil para dar formato al texto que aparece en un cuadro de mensaje.  
  
### <a name="remarks"></a>Comentarios  
 La primera forma de esta sobrecarga función muestra una cadena de texto que señala `lpszText` en el cuadro de mensaje y utiliza `nIDHelp` para describir un contexto de ayuda. El contexto de ayuda se utiliza para saltar a un tema de ayuda asociado cuando el usuario presiona la tecla de ayuda (normalmente F1).  
  
 La segunda forma de la función utiliza el recurso de cadena con el identificador `nIDPrompt` para mostrar un mensaje en el cuadro de mensaje. Se encontró la página de ayuda asociada a través del valor de `nIDHelp`. Si el valor predeterminado de `nIDHelp` es usado (-1), el identificador de recurso de cadena, `nIDPrompt`, se utiliza para el contexto de ayuda. Para obtener más información acerca de cómo definir los contextos de la Ayuda, consulte [28 de nota técnica](../../mfc/tn028-context-sensitive-help-support.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)
