---
title: "TN059: Usar macros de conversi&#243;n MBCS/Unicode de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conversión de macros [C++]"
  - "convertir Unicode"
  - "macros [C++], conversión de macros MBCS"
  - "MBCS [C++], conversión de macros"
  - "MFCANS32.DLL"
  - "TN059"
  - "Unicode [C++], conversión de macros"
  - "Unicode [C++], interfaces OLE"
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN059: Usar macros de conversi&#243;n MBCS/Unicode de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe cómo utilizar macros para la conversión de mbcs\/unicode, que se definen en AFXPRIV.H.  Estas macros son más útiles si la aplicación trata directamente de API OLE o por alguna razón, es a menudo convertir Unicode y MBCS.  
  
## Información general  
 En MFC 3.x, se utilizó un especial DLL \(MF CANS32 .DLL\) automáticamente para convertir Unicode y MBCS cuando las interfaces VIEJAS fueron llamadas.  Esta DLL es un nivel casi transparente que permitía que las aplicaciones OLE fueran escritas como si las API y las interfaces de OLE fueran MBCS, aunque siempre son Unicode \(excepto en Macintosh\).  Aunque este nivel era aplicaciones adecuadas y permitidas para ser portado rápidamente de Win16 a Win32 \(MFC, Microsoft Word, Microsoft Excel, y VBA, son solo algunas de las aplicaciones de Microsoft que utilizan esta tecnología\), tenía un acierto a veces de rendimiento significativo.  Por esta razón, MFC 4.x no utiliza esta DLL y en su lugar no habla directamente con interfaces de Unicode OLE.  Para ello, MFC debe convertir a Unicode a MBCS al realizar una llamada a una interfaz OLE, y necesita a menudo convertir a MBCS de Unicode al implementar una interfaz OLE.  Para administrar esto eficaz y fácilmente, varias macros se crearon para crear esta conversión más fácil.  
  
 Uno de los obstáculos mayores de crear para ese conjunto de macros es asignación de memoria.  Dado que las cadenas no pueden ser en contexto convertido, nueva memoria para contener los resultados convierten debe ser asignada.  Esto podría haber realizado con el código siguiente:  
  
```  
// we want to convert an MBCS string in lpszA  
int nLen = MultiByteToWideChar(CP_ACP, 0,lpszA, -1, NULL, NULL);  
LPWSTR lpszW = new WCHAR[nLen];  
MultiByteToWideChar(CP_ACP, 0,   
   lpszA, -1, lpszW, nLen);  
// use it to call OLE here  
pI->SomeFunctionThatNeedsUnicode(lpszW);  
// free the string  
delete[] lpszW;  
```  
  
 Este enfoque como varios problemas.  El mayor problema es que es mucho código a escribir, a probar, y depuración.  Algo que era una llamada de función simple, es mucho más complejo ahora.  Además, hay una sobrecarga significativa en tiempo de ejecución de esta manera.  Memoria tiene que ser asignada en el montón y ser por cada vez que se realiza una conversión.  Finalmente, el código anterior necesitaría tener `#ifdefs` adecuado agregado para las compilaciones de Unicode y Macintosh \(que no requieren esta conversión lugar\).  
  
 La solución que subimos con es crear algunas macros que 1\) la máscara la diferencia entre las distintas plataformas, y 2\) el uso un esquema de asignación de memoria eficaz, y 3\) son fáciles incrustar en código fuente existente.  A continuación se muestra un ejemplo de una de las definiciones:  
  
```  
#define A2W(lpa) (\  
    ((LPCSTR)lpa == NULL) ? NULL : (\  
          _convert = (strnlen(lpa)+1),\  
        AfxA2WHelper((LPWSTR) alloca(_convert*2),   
      lpa, _convert)\  
    )\  
)  
```  
  
 Utilizando esta macro en lugar del código anterior y cosas sea mucho más simple:  
  
```  
// use it to call OLE here  
USES_CONVERSION;  
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));  
```  
  
 Hay llamadas adicionales donde es necesaria la conversión, pero el uso macros es sencilla y eficaz.  
  
 La implementación de cada macro utiliza la función de \_alloca\(\) para asignar memoria del montón en lugar de la pila.  Asignar memoria de la pila es mucho más rápido que asignando memoria en la pila, y memoria automáticamente se libera cuando se sale de la función.  Además, las macros evitar llamar a **MultiByteToWideChar** \(o **WideCharToMultiByte**\) más de una vez.  Esto se hace asignando un poco más de memoria necesaria.  Sabemos que un MBC convertirá en al menos un **WCHAR** y que para cada **WCHAR** tendremos un máximo de dos bytes de MBC.  Asignando un poco más que lo necesario, pero siempre lo suficientemente controlar la conversión se evita la llamada de la segunda llamada segunda a la función de conversión.  La llamada a la aplicación auxiliar que la función **AfxA2Whelper** reduce el número de argumento inserta que se debe hacer para realizar la conversión \(esto da lugar a un código más pequeño, que si denominado **MultiByteToWideChar** directamente\).  
  
 Para que las macros tienen espacio para almacenar una longitud temporal, es necesario declarar una variable local denominada el \_convert que hace esto en cada función que use las macros de conversión.  Esto se hace invocando la macro de **USES\_CONVERSION** como se explica anteriormente en el ejemplo.  
  
 Hay dos macros genéricas de conversión y macros específicas VIEJAS.  Describen a estos dos conjuntos diferentes macros a continuación.  Todas las macros residen en AFXPRIV.H.  
  
## Macros genéricas de conversión  
 Las macros genéricas de conversión forman el mecanismo subyacente.  El ejemplo y la implementación macros mostrados en la sección anterior, A2W, es una como macro “genérica”.  No se relaciona con OLE específicamente.  Muestran el conjunto de macros genéricas a continuación:  
  
```  
A2CW      (LPCSTR) -> (LPCWSTR)  
A2W      (LPCSTR) -> (LPWSTR)  
W2CA      (LPCWSTR) -> (LPCSTR)  
W2A      (LPCWSTR) -> (LPSTR)  
```  
  
 Además de realizar conversiones de texto, también hay macros y funciones auxiliares para convertir `TEXTMETRIC`, `DEVMODE`, `BSTR`, y las cadenas asignadas OLE.  Estas macros están fuera del ámbito de este análisis – hace referencia a AFXPRIV.H para obtener más información sobre estas macros.  
  
## Macros VIEJAS de conversión  
 Las macros VIEJAS de conversión están diseñados específicamente para administrar las funciones que cuentan con caracteres de **OLESTR** .  Si examina los encabezados OLE, observará muchas referencias a **LPCOLESTR** y a **OLECHAR**.  Estos tipos se utilizan para hacer referencia al tipo de caracteres utilizados en interfaces VIEJAS de forma que no es específica de la plataforma.  Mapas de**OLECHAR** a `char` en plataformas de Win16 y Macintosh y a **WCHAR** en Win32.  
  
 Para conservar el número de directivas de **\#ifdef** en el código MFC a un mínimo tenemos una macro similar para cada conversión participe donde OLE cadenas.  Las macros siguientes se utilizan con frecuencia:  
  
```  
T2COLE   (LPCTSTR) -> (LPCOLESTR)  
T2OLE   (LPCTSTR) -> (LPOLESTR)  
OLE2CT   (LPCOLESTR) -> (LPCTSTR)  
OLE2T   (LPCOLESTR) -> (LPCSTR)  
```  
  
 Una vez más hay macros similares para hacer `TEXTMETRIC`, `DEVMODE`, `BSTR`, y las cadenas asignadas OLE.  Hace referencia a AFXPRIV.H para obtener más información.  
  
## Otras consideraciones  
 No use las macros en un bucle ajustado.  Por ejemplo, no desea escribir la clase siguiente de código:  
  
```  
void BadIterateCode(LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   for (int ii = 0; ii < 10000; ii++)  
      pI->SomeMethod(ii, T2COLE(lpsz));  
}  
```  
  
 En el código anterior puede dar lugar a asignar megabytes de memoria en la pila dependiendo de qué son el contenido de la cadena `lpsz` \!  También lleva tiempo para convertir la cadena en cada iteración del bucle.  En su lugar, mueva estas conversiones constantes del bucle:  
  
```  
void MuchBetterIterateCode(LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   LPCOLESTR lpszT = T2COLE(lpsz);  
   for (int ii = 0; ii < 10000; ii++)  
      pI->SomeMethod(ii, lpszT);  
}  
```  
  
 Si la cadena no es una constante, entonces encapsula la llamada al método en una función.  Esto permitirá al búfer de conversión es liberado cada vez.  Por ejemplo:  
  
```  
void CallSomeMethod(int ii, LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   pI->SomeMethod(ii, T2COLE(lpsz));  
}  
  
void MuchBetterIterateCode2(LPCTSTR* lpszArray)  
{  
   for (int ii = 0; ii < 10000; ii++)  
      CallSomeMethod(ii, lpszArray[ii]);  
}  
```  
  
 Nunca devuelve el resultado de una de las macros, a menos que el valor devuelto implica crear una copia de los datos antes de volver.  Por ejemplo, este código es incorrecta:  
  
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
  
 El código anterior podría corregir cambiando el valor devuelto algo que copia el valor:  
  
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
  
 Las macros son fáciles de utilizar y fáciles de incrustar en código, pero como puede indicar de las advertencias anterior, debe tener cuidado al utilizarlas.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)