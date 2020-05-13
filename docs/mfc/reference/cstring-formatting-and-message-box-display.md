---
title: Formato y presentación del cuadro de mensaje CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: fa1fe8826543834872de5257a0f5d56b2ad9fc1c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752673"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formato y presentación del cuadro de mensaje CString

Se proporcionan varias funciones para `CString` dar formato y analizar objetos. Puede utilizar estas funciones siempre `CString` que tenga que manipular objetos, pero son especialmente útiles para dar formato a las cadenas que aparecerán en el texto del cuadro de mensaje.

Este grupo de funciones también incluye una rutina global para mostrar un cuadro de mensaje.

### <a name="cstring-functions"></a>Funciones CString

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrae subcadenas separadas por un solo carácter de una cadena de origen determinada.|
|[AfxFormatString1](#afxformatstring1)|Sustituye una cadena determinada por los caracteres de formato "%1" en una cadena contenida en la tabla de cadenas.|
|[AfxFormatString2](#afxformatstring2)|Sustituye dos cadenas por los caracteres de formato "%1" y "%2" en una cadena contenida en la tabla de cadenas.|
|[AfxMessageBox](#afxmessagebox)|Muestra un cuadro de mensaje.|

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a>AfxExtractSubString

Esta función global se puede utilizar para extraer una subcadena de una cadena de origen determinada.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Referencia a un [CString](../../atl-mfc-shared/using-cstring.md) objeto que recibirá una subcadena individual.

*lpszFullString*<br/>
Cadena que contiene el texto completo de la cadena de la que se va a extraer.

*iSubString*<br/>
El índice de base cero de la subcadena que se va a extraer de *lpszFullString*.

*chSep*<br/>
Carácter separador utilizado para delimitar subcadenas.

### <a name="return-value"></a>Valor devuelto

TRUESi la función extrajo correctamente la subcadena en el índice proporcionado; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función es útil para extraer varias subcadenas de una cadena de origen cuando un carácter único conocido separa cada subcadena. Esta función busca desde el principio del parámetro *lpszFullString* cada vez que se llama.

Esta función devolverá FALSE si *lpszFullString* se establece en NULL o la función alcanza el final de *lpszFullString* sin encontrar *iSubString*+1 apariciones del carácter separador especificado. El parámetro *rString* no se modificará desde su valor original si *lpszFullString* se estableció en NULL; de lo contrario, el parámetro *rString* se establece en la cadena vacía si no se pudo extraer la subcadena para el índice especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1

Sustituye la cadena a la que apunta *lpsz1* por cualquier instancia de los caracteres "%1" en el recurso de cadena de plantilla identificado por *nIDS*.

```cpp
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Una referencia `CString` a un objeto que contendrá la cadena resultante después de realizar la sustitución.

*Nids*<br/>
El identificador de recurso de la cadena de plantilla en la que se realizará la sustitución.

*lpsz1*<br/>
Cadena que reemplazará los caracteres de formato "%1" en la cadena de plantilla.

### <a name="remarks"></a>Observaciones

La cadena recién formada se almacena en *rString*. Por ejemplo, si la cadena de la tabla de cadenas es "Archivo %1 no encontrado" y *lpsz1* es igual a "C:-MYFILE. TXT", a continuación, *rString* contendrá la cadena "Archivo C:-MYFILE. TXT no encontrado". Esta función es útil para dar formato a cadenas enviadas a cuadros de mensaje y otras ventanas.

Si los caracteres de formato "%1" aparecen en la cadena más de una vez, se realizarán varias sustituciones.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2

Sustituye la cadena señalada por *lpsz1* para cualquier instancia de los caracteres "%1", y la cadena señalada por *lpsz2* para cualquier instancia de los caracteres "%2", en el recurso de cadena de plantilla identificado por *nIDS*.

```cpp
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Una referencia `CString` a la que contendrá la cadena resultante después de realizar la sustitución.

*Nids*<br/>
El identificador de tabla de cadenas de la cadena de plantilla en la que se realizará la sustitución.

*lpsz1*<br/>
Cadena que reemplazará los caracteres de formato "%1" en la cadena de plantilla.

*lpsz2*<br/>
Cadena que reemplazará los caracteres de formato "%2" en la cadena de plantilla.

### <a name="remarks"></a>Observaciones

La cadena recién formada se almacena en *rString*. Por ejemplo, si la cadena de la tabla de cadenas es "Archivo %1 no se encuentra en el directorio %2", *lpsz1* apunta a "MYFILE. TXT", y *lpsz2* apunta a "C:-MYDIR", a continuación, *rString* contendrá la cadena "File MYFILE. TXT no se encuentra en el directorio C:-MYDIR"

Si los caracteres de formato "%1" o "%2" aparecen en la cadena más de una vez, se realizarán varias sustituciones. No tienen que estar en orden numérico.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox

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
Apunta a `CString` un objeto o cadena terminada en null que contiene el mensaje que se mostrará en el cuadro de mensaje.

*nType*<br/>
El estilo del cuadro de mensaje. Aplique cualquiera de los [estilos de cuadro de mensaje](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) al cuadro.

*nIDHelp*<br/>
El identificador de contexto de ayuda para el mensaje; 0 indica que se usará el contexto de Ayuda predeterminado de la aplicación.

*nIDPrompt*<br/>
Identificador único que se usa para hacer referencia a una cadena de la tabla de cadenas.

### <a name="return-value"></a>Valor devuelto

Cero si no hay suficiente memoria para mostrar el cuadro de mensaje; de lo contrario, se devuelve uno de los siguientes valores:

- IDABORT Se ha seleccionado el botón Anular.

- IDCANCEL Se ha seleccionado el botón Cancelar.

- IDIGNORE Se ha seleccionado el botón Ignorar.

- IDNO Se ha seleccionado el botón No.

- IDOK Se ha seleccionado el botón Aceptar.

- IDRETRY Se ha seleccionado el botón Reintentar.

- IDYES Se ha seleccionado el botón Sí.

Si un cuadro de mensaje tiene un botón Cancelar, se devolverá el valor IDCANCEL si se pulsa la tecla ESC o se selecciona el botón Cancelar. Si el cuadro de mensaje no tiene ningún botón Cancelar, presionar la tecla ESC no tiene ningún efecto.

Las funciones [AfxFormatString1](#afxformatstring1) y [AfxFormatString2](#afxformatstring2) pueden ser útiles para dar formato al texto que aparece en un cuadro de mensaje.

### <a name="remarks"></a>Observaciones

La primera forma de esta función sobrecargada muestra una cadena de texto señalada por *lpszText* en el cuadro de mensaje y usa *nIDHelp* para describir un contexto de Ayuda. El contexto de Ayuda se usa para saltar a un tema de Ayuda asociado cuando el usuario presiona la tecla Ayuda (normalmente F1).

La segunda forma de la función utiliza el recurso de cadena con el identificador *nIDPrompt* para mostrar un mensaje en el cuadro de mensaje. La página de Ayuda asociada se encuentra a través del valor de *nIDHelp*. Si se utiliza el valor predeterminado de *nIDHelp* (-1), el identificador de recurso de cadena, *nIDPrompt*, se utiliza para el contexto de ayuda. Para obtener más información sobre la definición de contextos de ayuda, consulte [Nota técnica 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Clase CStringT](../../atl-mfc-shared/reference/cstringt-class.md)
