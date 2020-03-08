---
title: Formato y presentación del cuadro de mensaje CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: ad880c5302fd2274c5d46719e912461fd7497f10
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854084"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formato y presentación del cuadro de mensaje CString

Se proporcionan varias funciones para dar formato y analizar `CString` objetos. Puede usar estas funciones siempre que tenga que manipular `CString` objetos, pero resultan especialmente útiles para dar formato a las cadenas que aparecerán en el texto del cuadro de mensaje.

Este grupo de funciones también incluye una rutina global para mostrar un cuadro de mensaje.

### <a name="cstring-functions"></a>Funciones de CString

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrae las subcadenas separadas por un único carácter de una cadena de origen determinada.|
|[AfxFormatString1](#afxformatstring1)|Sustituye una cadena determinada por los caracteres de formato "%1" en una cadena incluida en la tabla de cadenas.|
|[AfxFormatString2](#afxformatstring2)|Sustituye dos cadenas para los caracteres de formato "%1" y "%2" en una cadena incluida en la tabla de cadenas.|
|[AfxMessageBox](#afxmessagebox)|Muestra un cuadro de mensaje.|

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

##  <a name="afxextractsubstring"></a>AfxExtractSubString

Esta función global se puede usar para extraer una subcadena de una cadena de origen determinada.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Referencia a un objeto [CString](../../atl-mfc-shared/using-cstring.md) que recibirá una subcadena individual.

*lpszFullString*<br/>
Cadena que contiene el texto completo de la cadena de la que se va a extraer.

*iSubString*<br/>
Índice de base cero de la subcadena que se va a extraer de *lpszFullString*.

*chSep*<br/>
Carácter separador utilizado para delimitar las subcadenas.

### <a name="return-value"></a>Valor devuelto

TRUE si la función extrajo correctamente la subcadena en el índice proporcionado; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función es útil para extraer varias subcadenas de una cadena de origen cuando un carácter individual conocido separa cada subcadena. Esta función realiza una búsqueda desde el principio del parámetro *lpszFullString* cada vez que se llama.

Esta función devolverá FALSE si *lpszFullString* está establecido en null o la función alcanza el final de *LpszFullString* sin encontrar *iSubString*+ 1 repeticiones del carácter separador especificado. El parámetro *rString* no se modificará de su valor original si *lpszFullString* se estableció en null; de lo contrario, el parámetro *rString* se establece en la cadena vacía si no se pudo extraer la subcadena para el índice especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

##  <a name="afxformatstring1"></a>AfxFormatString1

Sustituye la cadena a la que señala *lpsz1* por cualquier instancia de los caracteres "%1" en el recurso de cadena de plantilla identificado por *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Referencia a un objeto `CString` que contendrá la cadena resultante una vez realizada la sustitución.

*nIDS*<br/>
El identificador de recurso de la cadena de plantilla en la que se realizará la sustitución.

*lpsz1*<br/>
Cadena que reemplazará los caracteres de formato "%1" en la cadena de la plantilla.

### <a name="remarks"></a>Observaciones

La cadena recién formada se almacena en *rString*. Por ejemplo, si la cadena de la tabla de cadenas es "File %1 not found", y *lpsz1* es igual a "C:\MYFILE. TXT ", *rString* contendrá la cadena" File C:\MYFILE. TXT no encontrado ". Esta función es útil para dar formato a las cadenas enviadas a los cuadros de mensaje y a otras ventanas.

Si los caracteres de formato "%1" aparecen en la cadena más de una vez, se realizarán varias sustituciones.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

##  <a name="afxformatstring2"></a>AfxFormatString2

Sustituye la cadena a la que señala *lpsz1* para cualquier instancia de los caracteres "%1" y la cadena a la que apunta *lpsz2* para cualquier instancia de los caracteres "%2", en el recurso de cadena de plantilla identificado por *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Referencia al `CString` que contendrá la cadena resultante una vez realizada la sustitución.

*nIDS*<br/>
IDENTIFICADOR de la tabla de cadenas de la cadena de la plantilla en la que se realizará la sustitución.

*lpsz1*<br/>
Cadena que reemplazará los caracteres de formato "%1" en la cadena de la plantilla.

*lpsz2*<br/>
Cadena que reemplazará los caracteres de formato "%2" en la cadena de la plantilla.

### <a name="remarks"></a>Observaciones

La cadena recién formada se almacena en *rString*. Por ejemplo, si la cadena de la tabla de cadenas es "File %1 not found in Directory %2", *lpsz1* señala a "Perfile. TXT ", y *lpsz2* apuntan a" c:\MiDir "; luego, *rString* contendrá la cadena" File Perfile. TXT no encontrado en el directorio C:\MIDIR "

Si los caracteres de formato "%1" o "%2" aparecen en la cadena más de una vez, se realizarán varias sustituciones. No es necesario que estén en orden numérico.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

##  <a name="afxmessagebox"></a>AfxMessageBox

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

*lpszText*<br/>
Señala a un objeto `CString` o a una cadena terminada en null que contiene el mensaje que se va a mostrar en el cuadro de mensaje.

*nType*<br/>
Estilo del cuadro de mensaje. Aplique cualquiera de los [estilos de cuadro de mensaje](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) al cuadro.

*nIDHelp*<br/>
IDENTIFICADOR del contexto de ayuda para el mensaje; 0 indica que se utilizará el contexto de ayuda predeterminado de la aplicación.

*nIDPrompt*<br/>
IDENTIFICADOR único que se usa para hacer referencia a una cadena en la tabla de cadenas.

### <a name="return-value"></a>Valor devuelto

Cero si no hay suficiente memoria para mostrar el cuadro de mensaje; de lo contrario, se devuelve uno de los valores siguientes:

- IDABORT se seleccionó el botón anular.

- IDCANCEL se seleccionó el botón Cancelar.

- IDIGNORE se seleccionó el botón Omitir.

- IDNO se seleccionó el botón no.

- IDOK se seleccionó el botón Aceptar.

- IDRETRY se seleccionó el botón Reintentar.

- IDYES se seleccionó el botón sí.

Si un cuadro de mensaje tiene un botón Cancelar, el valor IDCANCEL se devolverá si se presiona la tecla ESC o se selecciona el botón Cancelar. Si el cuadro de mensaje no tiene un botón Cancelar, presionar la tecla ESC no tiene ningún efecto.

Las funciones [AfxFormatString1](#afxformatstring1) y [AfxFormatString2](#afxformatstring2) pueden ser útiles para dar formato al texto que aparece en un cuadro de mensaje.

### <a name="remarks"></a>Observaciones

La primera forma de esta función sobrecargada muestra una cadena de texto a la que señala *lpszText* en el cuadro de mensaje y usa *nIDHelp* para describir un contexto de ayuda. El contexto de ayuda se usa para saltar a un tema de ayuda asociado cuando el usuario presiona la tecla de ayuda (normalmente F1).

La segunda forma de la función utiliza el recurso de cadena con el identificador *nIDPrompt* para mostrar un mensaje en el cuadro de mensaje. La página de ayuda asociada se encuentra en el valor de *nIDHelp*. Si se usa el valor predeterminado de *nIDHelp* (-1), se usa el identificador de recurso de cadena, *nIDPrompt*, para el contexto de ayuda. Para obtener más información sobre cómo definir contextos de ayuda, vea la [Nota técnica 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)
