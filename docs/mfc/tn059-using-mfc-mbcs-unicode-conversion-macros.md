---
title: 'TN059: Uso de macros de conversión MBCS-Unicode de MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: 0d63a87d0fddde30dd5cbb18207297a345d74b9c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366591"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Usar macros de conversión MBCS/Unicode de MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe cómo utilizar las macros para la conversión MBCS/Unicode, que se definen en AFXPRIV. H. Estas macros son más útiles si la aplicación se ocupa directamente de la API OLE o, por alguna razón, a menudo necesita convertir entre Unicode y MBCS.

## <a name="overview"></a>Información general

En MFC 3.x, se utilizó un archivo DLL especial (MFCANS32. DLL) para convertir automáticamente entre Unicode y MBCS cuando se llamó a interfaces OLE. Este archivo DLL era una capa casi transparente que permitía escribir aplicaciones OLE como si las interfaces y las API OLE fueran MBCS, aunque siempre sean Unicode (excepto en Macintosh). Aunque esta capa era conveniente y permitía que las aplicaciones se portasen rápidamente de Win16 a Win32 (MFC, Microsoft Word, Microsoft Excel y VBA, son solo algunas de las aplicaciones de Microsoft que usaron esta tecnología), tuvo un impacto en el rendimiento a veces significativo. Por este motivo, MFC 4.x no utiliza este archivo DLL y, en su lugar, se conecta directamente con las interfaces OLE Unicode. Para ello, MFC necesita convertir a Unicode a MBCS al realizar una llamada a una interfaz OLE y, a menudo, necesita convertir a MBCS desde Unicode al implementar una interfaz OLE. Con el fin de manejar esto de manera eficiente y fácil, se crearon una serie de macros para facilitar esta conversión.

Uno de los mayores obstáculos de crear un conjunto de macros de este tipo es la asignación de memoria. Dado que las cadenas no se pueden convertir en su lugar, se debe asignar nueva memoria para contener los resultados convertidos. Esto podría haberse hecho con código similar al siguiente:

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

Este enfoque como una serie de problemas. El problema principal es que es una gran cantidad de código para escribir, probar y depurar. Algo que era una simple llamada de función, ahora es mucho más complejo. Además, hay una sobrecarga de tiempo de ejecución significativa al hacerlo. La memoria tiene que ser asignada en el montón y liberada cada vez que se realiza una conversión. Por último, el código anterior `#ifdefs` tendría que tener agregado adecuado para las compilaciones Unicode y Macintosh (que no requieren que esta conversión tenga lugar).

La solución que se nos ocurrió es crear algunas macros que 1) enmascarar la diferencia entre las diversas plataformas, y 2) utilizar un esquema de asignación de memoria eficiente, y 3) son fáciles de insertar en el código fuente existente. A continuación se muestra un ejemplo de una de las definiciones:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Usando esta macro en lugar del código anterior y las cosas son mucho más simples:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Hay llamadas adicionales donde la conversión es necesaria, pero el uso de las macros es simple y eficaz.

La implementación de cada macro utiliza la función _alloca() para asignar memoria desde la pila en lugar del montón. La asignación de memoria de la pila es mucho más rápida que la asignación de memoria en el montón y la memoria se libera automáticamente cuando se cierra la función. Además, las `MultiByteToWideChar` macros `WideCharToMultiByte`evitan llamar (o ) más de una vez. Esto se hace asignando un poco más de memoria de la necesaria. Sabemos que un MBC se convertirá en como máximo un **WCHAR** y que por cada **WCHAR** tendremos un máximo de dos bytes MBC. Al asignar un poco más de lo necesario, pero siempre lo suficiente para controlar la conversión, se evita la segunda llamada a la función de conversión. La llamada a `AfxA2Whelper` la función auxiliar reduce el número de inserciones de argumento según las `MultiByteToWideChar` que se deben realizar para realizar la conversión (esto da como resultado código más pequeño, que si se llama directamente).

Para que las macros tengan espacio para almacenar la longitud temporal, es necesario declarar una variable local denominada _convert que lo hace en cada función que utiliza las macros de conversión. Esto se hace invocando la macro USES_CONVERSION como se ve arriba en el ejemplo.

Hay macros de conversión genéricas y macros específicas OLE. Estos dos conjuntos de macros diferentes se describen a continuación. Todas las macros residen en AFXPRIV. H.

## <a name="generic-conversion-macros"></a>Macros de conversión genéricas

Las macros de conversión genéricas forman el mecanismo subyacente. El ejemplo de macro y la implementación que se muestra en la sección anterior, A2W, es una de esas macros "genéricas". No está relacionado con OLE específicamente. El conjunto de macros genéricas se enumera a continuación:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Además de realizar conversiones de texto, también `TEXTMETRIC` `DEVMODE`hay `BSTR`macros y funciones auxiliares para convertir cadenas asignadas, , y OLE. Estas macros están fuera del alcance de esta discusión - consulte AFXPRIV. H para obtener más información sobre esas macros.

## <a name="ole-conversion-macros"></a>Macros de conversión OLE

Las macros de conversión OLE están diseñadas específicamente para controlar funciones que esperan **caracteres OLESTR.** Si examina los encabezados OLE, verá muchas referencias a **LPCOLESTR** y **OLECHAR**. Estos tipos se utilizan para hacer referencia al tipo de caracteres utilizados en las interfaces OLE de una manera que no es específica de la plataforma. **OLECHAR** se asigna a **char** en las plataformas Win16 y Macintosh y **WCHAR** en Win32.

Para mantener el número de **directivas #ifdef** en el código MFC al mínimo, tenemos una macro similar para cada conversión que donde están implicadas las cadenas OLE. Las siguientes macros son las más utilizadas:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Una vez más, hay macros similares para realizar cadenas asignadas a TEXTMETRIC, DEVMODE, BSTR y OLE. Consulte AFXPRIV. H para más información.

## <a name="other-considerations"></a>Otras consideraciones

No utilice las macros en un bucle estrecho. Por ejemplo, no desea escribir el siguiente tipo de código:

```
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

¡El código anterior podría dar lugar a la asignación de megabytes `lpsz` de memoria en la pila dependiendo de cuál sea el contenido de la cadena! También toma tiempo convertir la cadena para cada iteración del bucle. En su lugar, mueva tales conversiones constantes fuera del bucle:

```
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Si la cadena no es constante, encapsular la llamada al método en una función. Esto permitirá liberar el búfer de conversión cada vez. Por ejemplo:

```
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

Nunca devuelva el resultado de una de las macros, a menos que el valor devuelto implique realizar una copia de los datos antes de la devolución. Por ejemplo, este código es malo:

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

El código anterior podría corregirse cambiando el valor devuelto a algo que copie el valor:

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

Las macros son fáciles de usar y fáciles de insertar en el código, pero como se puede ver en las advertencias anteriores, debe tener cuidado al usarlas.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
