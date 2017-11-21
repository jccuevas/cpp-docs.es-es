---
title: "TN059: Usar Macros de conversión de Unicode a MBCS de MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.mbcs
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30872fc89ad51305630b6f9b64245a529c017cb7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Usar macros de conversión MBCS/Unicode de MFC
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo utilizar las macros de conversión de MBCS/Unicode, que se definen en AFXPRIV. H. Estas macros son muy útiles si sus negocios de la aplicación directamente con la API de OLE o por algún motivo, a menudo es necesario convertir entre Unicode y MBCS.  
  
## <a name="overview"></a>Información general  
 En MFC 3.x, era de un archivo DLL especial utilizado (MFCANS32. (DLL) para la conversión automática entre Unicode y MBCS cuando se llamaron a interfaces OLE. Este archivo DLL era una capa transparente casi que permitía a las aplicaciones de OLE que escribirse como si las API OLE e interfaces fueron MBCS, aunque siempre son Unicode (excepto en los equipos Macintosh). Durante esta capa cómoda y permite a las aplicaciones se pasar rápidamente de Win16 a Win32 (MFC, Microsoft Word, Microsoft Excel y VBA, son solo algunas de las aplicaciones de Microsoft que utilizan esta tecnología), tenía un rendimiento significativo a veces de aciertos. Por esta razón, MFC 4.x no usa este archivo DLL y en su lugar se comunica directamente con las interfaces OLE de Unicode. Para ello, MFC debe convertir a Unicode a MBCS cuando se realiza una llamada a una interfaz OLE y, a menudo es necesario convertir a MBCS de Unicode al implementar una interfaz OLE. Para solucionar esto con eficacia y facilidad, se crearon varias macros para facilitar esta conversión.  
  
 Uno de los mayores obstáculos de creación de este tipo de un conjunto de macros es la asignación de memoria. Dado que las cadenas no se puede convertir en su lugar, se debe asignar nueva memoria para almacenar los resultados de convertir. Esto podría haberse realizado con código similar al siguiente:  
  
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
  
 Este enfoque como una serie de problemas. El problema principal es que es una gran cantidad de código para escribir, probar y depurar. Algo que se produjo una llamada de función simple, ahora es mucho más complejo. Además, hay un tiempo de ejecución importante sobrecarga en hacerlo. Memoria debe asignar en el montón y liberar cada vez que se realiza una conversión. Por último, el código anterior es necesario que adecuado `#ifdefs` agregada para las compilaciones de Unicode y Macintosh (que no requieren esta conversión tenga lugar).  
  
 La solución con que se ha aparecido consiste en crear algunas macros qué máscara de (1) la diferencia entre las diversas plataformas y (2) utilice un esquema de asignación de memoria eficaz y (3) son fácil de insertar en las existentes de código fuente. Este es un ejemplo de una de las definiciones:  
  
```  
#define A2W(lpa) (\  
 ((LPCSTR)lpa == NULL) NULL : (\  
    _convert = (strnlen(lpa)+1),\  
    AfxA2WHelper((LPWSTR) alloca(_convert*2),   
    lpa,
    _convert)\)\)  
```  
  
 Con esta macro en lugar del código anterior y las cosas son mucho más fácil:  
  
```  
// use it to call OLE here  
USES_CONVERSION;  
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```  
  
 Hay llamadas adicionales donde es necesario realizar conversión, pero el uso de las macros es sencilla y eficaz.  
  
 La implementación de cada macro usa la función de _alloca () para asignar memoria de la pila en lugar del montón. Asignación de memoria de la pila es mucho más rápida que la asignación de memoria en el montón y la memoria se libera automáticamente cuando se sale de la función. Además, las macros evite llamar a **MultiByteToWideChar** (o **WideCharToMultiByte**) más de una vez. Esto se debe asignar un poco más memoria que es necesario. Sabemos que un MBC convertirá en al menos uno **WCHAR** y que, para cada uno de ellos **WCHAR** tenemos un máximo de dos bytes MBC. Asignando un poco más de lo necesario, pero el siempre suficiente para administrar la segunda llamada a la conversión en segundo lugar se evita la llamada a la función de conversión. La llamada a la función auxiliar **AfxA2Whelper** reduce el número de inserciones de argumento que debe realizarse para realizar la conversión (Esto produce un código más pequeño, que si llama **MultiByteToWideChar**directamente).  
  
 En orden a las macros tienen espacio para almacenar la longitud temporal, es necesario declarar una variable local denominada _convertir que lo haga en cada función que utiliza las macros de conversión. Esto se realiza invocando la **USES_CONVERSION** macro tal como se muestra anteriormente en el ejemplo.  
  
 Hay macros de conversión genérico y macros específicas de OLE. A continuación se comentan estos dos conjuntos diferentes de macro. Todas las macros residen en AFXPRIV. H.  
  
## <a name="generic-conversion-macros"></a>Macros de conversión genérico  
 Las macros de conversión genérico forman el mecanismo subyacente. El ejemplo de macro y la implementación se muestra en la sección anterior, A2W, es un tal macro "genérica". No está relacionado a OLE específicamente. El conjunto de macros genéricos se menciona a continuación:  
  
```  
A2CW      (LPCSTR) -> (LPCWSTR)  
A2W      (LPCSTR) -> (LPWSTR)  
W2CA      (LPCWSTR) -> (LPCSTR)  
W2A      (LPCWSTR) -> (LPSTR)  
```  
  
 Además de realizar conversiones de texto, también hay macros y funciones auxiliares para convertir `TEXTMETRIC`, `DEVMODE`, `BSTR`y asignada cadenas OLE. Estas macros están fuera del ámbito de este análisis: hacer referencia a AFXPRIV. H para obtener más información sobre las macros.  
  
## <a name="ole-conversion-macros"></a>Macros de conversión de OLE  
 Las macros de conversión de OLE están diseñadas específicamente para controlar las funciones que esperan **OLESTR** caracteres. Si examina los encabezados OLE, verá muchas referencias a **LPCOLESTR** y **OLECHAR**. Estos tipos se utilizan para hacer referencia al tipo de caracteres que se utilizan en las interfaces OLE de forma que no es específico de la plataforma. **OLECHAR** se asigna a `char` en plataformas Win16 y Macintosh y **WCHAR** en Win32.  
  
 Con el fin de mantener el número de **#ifdef** directivas en la MFC de código al mínimo tenemos una macro similar en cada conversión que cuando se trate de cadenas OLE. Se usan más habitualmente las macros siguientes:  
  
```  
T2COLE   (LPCTSTR) -> (LPCOLESTR)  
T2OLE   (LPCTSTR) -> (LPOLESTR)  
OLE2CT   (LPCOLESTR) -> (LPCTSTR)  
OLE2T   (LPCOLESTR) -> (LPCSTR)  
```  
  
 De nuevo, hay macros similar para hacerlo `TEXTMETRIC`, `DEVMODE`, `BSTR`y asignada cadenas OLE. Consulte AFXPRIV. H para obtener más información.  
  
## <a name="other-considerations"></a>Otras consideraciones  
 No use las macros en un bucle ajustado. Por ejemplo, no desea escribir el tipo de código siguiente:  
  
```  
void BadIterateCode(LPCTSTR lpsz)  
{  
    USES_CONVERSION; 
    for (int ii = 0; ii <10000; ii++)  
    pI->SomeMethod(ii, T2COLE(lpsz));

}  
```  
  
 El código anterior podría producir en la asignación de megabytes de memoria en la pila dependiendo de qué el contenido de la cadena `lpsz` es! También toma un tiempo para convertir la cadena para cada iteración del bucle. En su lugar, mover estas conversiones constantes fuera del bucle:  
  
```  
void MuchBetterIterateCode(LPCTSTR lpsz)  
{  
    USES_CONVERSION; 
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)  
    pI->SomeMethod(ii, lpszT);

}  
```  
  
 Si la cadena no es constante, a continuación, encapsular la llamada de método en una función. Esto permitirá que el búfer de conversión que se libere cada vez. Por ejemplo:  
  
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
  
 Nunca devuelve el resultado de una de las macros, a menos que el valor devuelto implica realizar una copia de los datos antes de la devolución. Por ejemplo, este código es incorrecto:  
  
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
  
 El código anterior podría corregirse cambiando el valor devuelto en un valor que se copia el valor:  
  
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
  
 Las macros son fáciles de usar y fáciles de insertar en el código, pero como puede imaginar desde las advertencias anteriores, debe tener cuidado cuando se usen.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

