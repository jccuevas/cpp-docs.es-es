---
title: Formato CString y presentación del cuadro de mensaje | Microsoft Docs
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
ms.openlocfilehash: 125d0d3ec1549b9eba46cbfebfb7ecfe2c2186d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387190"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formato y presentación del cuadro de mensaje CString

Se proporciona una serie de funciones para dar formato y analizar `CString` objetos. Puede usar estas funciones siempre tiene que manipular `CString` objetos, pero son especialmente útiles para dar formato a cadenas que aparecerán en el cuadro de mensaje de texto.

Este grupo de funciones también incluye una rutina global para mostrar un cuadro de mensaje.

### <a name="cstring-functions"></a>Funciones de CString

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrae las subcadenas separadas por un único carácter de una cadena de origen especificado.|
|[AfxFormatString1](#afxformatstring1)|Sustituye una cadena determinada para los caracteres de formato "%1" en una cadena de contenido en la tabla de cadenas.|
|[AfxFormatString2](#afxformatstring2)|Las cadenas de dos sustitutos para el formato de caracteres "%1" y "%2" en una cadena de contenido en la tabla de cadenas.|
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

*rString*<br/>
Hacer referencia a un [CString](../../atl-mfc-shared/using-cstring.md) objeto que recibirá una subcadena individual.

*lpszFullString*<br/>
Cadena que contiene el texto completo de la cadena para extraer.

*iSubString*<br/>
Índice de base cero de la subcadena que se va a extraer de *lpszFullString*.

*chSep*<br/>
Carácter de separador utilizado para delimitar las subcadenas.

### <a name="return-value"></a>Valor devuelto

TRUE si la función extrae correctamente la subcadena en el índice proporcionado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Esta función es útil para extraer varias subcadenas de una cadena de origen cuando un único carácter conocido separa cada subcadena. Esta función busca desde el principio de la *lpszFullString* parámetro cada vez que se llama.

Esta función devuelve FALSE si *lpszFullString* se establece en NULL o la función llega al final de *lpszFullString* sin buscar *iSubString*+ 1 repeticiones del carácter separador especificado. El *rString* parámetro no se modificarán de su valor original si *lpszFullString* se estableció en NULL; de lo contrario, el *rString* parámetro se establece en una cadena vacía si no se pudo extraer la subcadena para el índice especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

##  <a name="afxformatstring1"></a>  AfxFormatString1

Sustituye la cadena señalada por *lpsz1* para todas las instancias de los caracteres "%1" en el recurso de cadena de plantilla identificado por *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Una referencia a un `CString` objeto que va a contener la cadena resultante después de realiza la sustitución.

*nIDS*<br/>
El identificador de recurso de la cadena de plantilla en el que se realizará la sustitución.

*lpsz1*<br/>
Cadena que va a reemplazar el formato de caracteres "%1" en la cadena de plantilla.

### <a name="remarks"></a>Comentarios

La cadena recién formada se almacena en *rString*. Por ejemplo, si la cadena en la tabla de cadenas es "Archivo %1 no encontrado", y *lpsz1* es igual a "C:\MYFILE. TXT", a continuación, *rString* contendrá la cadena"File C:\MYFILE. TXT no encontrado". Esta función es útil para dar formato a las cadenas enviadas a los cuadros de mensajes y otras ventanas.

Si los caracteres de formato "%1" no aparecen en la cadena de más de una vez, se realizarán varias sustituciones.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

##  <a name="afxformatstring2"></a>  AfxFormatString2

Sustituye la cadena señalada por *lpsz1* para todas las instancias de los caracteres "%1" y la cadena señalada por *lpsz2* para todas las instancias de los caracteres "%2", en el recurso de cadena de plantilla identificado por *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Una referencia a la `CString` que contendrá la cadena resultante después de realiza la sustitución.

*nIDS*<br/>
Id. de tabla de cadena de la cadena de plantilla en el que se realizará la sustitución.

*lpsz1*<br/>
Cadena que va a reemplazar el formato de caracteres "%1" en la cadena de plantilla.

*lpsz2*<br/>
Cadena que va a reemplazar el formato de caracteres "%2" en la cadena de plantilla.

### <a name="remarks"></a>Comentarios

La cadena recién formada se almacena en *rString*. Por ejemplo, si la cadena en la tabla de cadenas es "Archivo %1 no se encuentra en el directorio %2", *lpsz1* apunta a "MYFILE. "TXT", y *lpsz2* apunta a "C:\MYDIR", a continuación, *rString* contendrá la cadena "File MYFILE. No se encuentra en el directorio C:\MYDIR "TXT"

Si el formato de caracteres "%1" o "%2" no aparece en la cadena de más de una vez, se realizarán varias sustituciones. No tienen que estar en orden numérico.

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

*lpszText*<br/>
Apunta a un `CString` objeto o una cadena terminada en null que contiene el mensaje que se mostrará en el cuadro de mensaje.

*nLas*<br/>
El estilo del cuadro de mensaje. Aplicar cualquiera de los [estilos de cuadro de mensaje](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) al cuadro.

*nIDHelp*<br/>
El identificador de contexto de ayuda para el mensaje; 0 indica que se utilizará el contexto de Ayuda de la aplicación.

*nIDPrompt*<br/>
Un identificador único que se usa para hacer referencia a una cadena en la tabla de cadenas.

### <a name="return-value"></a>Valor devuelto

Cero si no hay memoria suficiente para mostrar el cuadro de mensaje; en caso contrario, se devuelve uno de los siguientes valores:

- Se seleccionó IDABORT el botón Anular.

- Se seleccionó IDCANCEL el botón Cancelar.

- Se seleccionó IDIGNORE el botón Omitir.

- IDNO el botón No se ha seleccionado.

- Se seleccionó IDOK el botón Aceptar.

- Se seleccionó IDRETRY el botón Reintentar.

- Se seleccionó IDYES el botón Sí.

Si un cuadro de mensaje tiene un botón Cancelar, se devolverá el valor IDCANCEL si se presiona la tecla ESC o se selecciona el botón Cancelar. Si el cuadro de mensaje no tiene ningún botón Cancelar, presionar la tecla ESC tiene ningún efecto.

Las funciones [AfxFormatString1](#afxformatstring1) y [AfxFormatString2](#afxformatstring2) puede ser útil para dar formato al texto que aparece en un cuadro de mensaje.

### <a name="remarks"></a>Comentarios

El primer formulario de esta función sobrecargada muestra una cadena de texto apunta *lpszText* en el cuadro de mensaje y utiliza *nIDHelp* para describir un contexto de ayuda. El contexto de ayuda se utiliza para saltar a un tema de ayuda asociado cuando el usuario presiona la tecla de ayuda (normalmente F1).

La segunda forma de la función usa el recurso de cadena con el Id. de *nIDPrompt* para mostrar un mensaje en el cuadro de mensaje. Se encuentra la página de ayuda asociada con el valor de *nIDHelp*. Si el valor predeterminado de *nIDHelp* es utilizado (-1), el identificador de recurso de cadena, *nIDPrompt*, se usa para el contexto de ayuda. Para obtener más información acerca de cómo definir contextos de ayuda, consulte [Nota técnica 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)
