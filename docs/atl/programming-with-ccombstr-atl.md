---
title: "Programar con CComBSTR (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComBSTR (clase), programar"
  - "Unicode, usar CComBSTR [ATL]"
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Programar con CComBSTR (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase [CComBSTR](../atl/reference/ccombstr-class.md) ATL proporciona un contenedor alrededor del tipo de datos de `BSTR` .  Mientras `CComBSTR` es una herramienta útil, hay varias situaciones que requieren precaución.  
  
-   [problemas de conversión](#programmingwithccombstr_conversionissues)  
  
-   [Problemas de ámbito](#programmingwithccombstr_scopeissues)  
  
-   [Liberar explícitamente el objeto CComBSTR](#programmingwithccombstr_explicitlyfreeing)  
  
-   [Utilizar objetos CComBSTR en bucles](#programmingwithccombstr_usingloops)  
  
-   [Problemas de pérdida de memoria](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a> problemas de conversión  
 Aunque varios métodos de `CComBSTR` automáticamente convierten un argumento de cadena ANSI en Unicode, los métodos devolverán siempre las cadenas de formato Unicode.  Para convertir la cadena de resultados a ANSI, utilice una clase de conversión de ATL.  Para obtener más información sobre los tipos de conversión ATL, vea [Macros de conversión de cadena ATL y MFC](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md).  
  
### Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/CPP/programming-with-ccombstr-atl_1.cpp)]  
  
 Si está utilizando un literal de cadena para modificar un objeto de `CComBSTR` , utilice cadenas de caracteres anchos.  esto reducirá conversiones innecesarias.  
  
### Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/CPP/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a> Problemas de ámbito  
 Como con cualquier buena clase, `CComBSTR` libere los recursos cuando sale del ámbito.  Si una función devuelve un puntero a la cadena de `CComBSTR` , pueden producirse problemas, como el puntero hará referencia a memoria que ya se ha liberado.  En estos casos, utilice el método de **Copiar** , como se muestra a continuación.  
  
### Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/CPP/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a> Liberar explícitamente el objeto CComBSTR  
 Es posible liberar explícitamente la cadena contenida en el objeto de `CComBSTR` antes de que el objeto ámbito.  Si se libera la cadena, el objeto de `CComBSTR` no es válido.  
  
### Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/CPP/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a> Utilizar objetos CComBSTR en bucles  
 Como la clase de `CComBSTR` asigna un búfer para realizar ciertas operaciones, como el operador de `+=` o el método de **Anexar** , no se recomienda realiza la manipulación de cadenas dentro de un bucle ajustado.  en estas situaciones, `CStringT` proporciona mejor rendimiento.  
  
### Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/CPP/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a> Problemas de pérdida de memoria  
 Pasar a la dirección de `CComBSTR` inicializarse con una función como parámetro de **\[out\]** provoca una pérdida de memoria.  
  
 En el ejemplo siguiente, la cadena asignada para contener la cadena `"Initialized"` se bloquee cuando la función `MyGoodFunction` reemplaza la cadena.  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/CPP/programming-with-ccombstr-atl_6.cpp)]  
  
 Para evitar la pérdida, llame al método de **Vacío** en los objetos existentes de `CComBSTR` antes de pasar la dirección como parámetro de **\[out\]** .  
  
 Observe que el mismo código no produciría un escape si el parámetro de la función es **\[in, out\]**.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../Topic/wstring.md)   
 [String Conversion Macros](../atl/reference/string-conversion-macros.md)