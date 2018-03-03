---
title: Programar con CComBSTR (ATL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8f496dd73c2d15f8f78ddbdc205f31a8520c674
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="programming-with-ccombstr-atl"></a>Programar con CComBSTR (ATL)
La clase ATL [CComBSTR](../atl/reference/ccombstr-class.md) proporciona un contenedor alrededor del `BSTR` tipo de datos. Mientras `CComBSTR` es una herramienta útil, hay varias situaciones que requieren precaución.  
  
-   [Problemas de conversión](#programmingwithccombstr_conversionissues)  
  
-   [Problemas de ámbito](#programmingwithccombstr_scopeissues)  
  
-   [Liberar explícitamente el objeto CComBSTR](#programmingwithccombstr_explicitlyfreeing)  
  
-   [Utilizar objetos CComBSTR en bucles](#programmingwithccombstr_usingloops)  
  
-   [Problemas de pérdidas de memoria](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a>Problemas de conversión  
 Aunque varias `CComBSTR` métodos convertirán automáticamente un argumento de cadena ANSI a Unicode, los métodos siempre devolverán cadenas de formato Unicode. Para convertir la cadena de salida a ANSI, use una clase de conversión de ATL. Para obtener más información sobre las clases de conversión de ATL, vea [Macros de conversión de cadena de MFC y ATL](reference/string-conversion-macros.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]  
  
 Si utilizas un literal de cadena para modificar un `CComBSTR` objeto, utilice las cadenas de caracteres anchos. Esto reducirá las conversiones innecesarias.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a>Problemas de ámbito  
 Al igual que con cualquier clase con buen comportamiento, `CComBSTR` liberará sus recursos cuando sale del ámbito. Si una función devuelve un puntero a la `CComBSTR` cadena, esto puede causar problemas, como el puntero hará referencia a memoria que ya se ha liberado. En estos casos, use la **copia** método, tal y como se muestra a continuación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a>Liberar explícitamente el objeto CComBSTR  
 Es posible liberar explícitamente la cadena contenida en el `CComBSTR` objeto antes de que el objeto queda fuera de ámbito. Si la cadena se libera, el `CComBSTR` objeto no es válido.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a>Utilizar objetos CComBSTR en bucles  
 Como el `CComBSTR` clase asigna un búfer para realizar ciertas operaciones, como el `+=` operador o **anexado** método, no se recomienda que lleva a cabo la manipulación de cadenas dentro de un bucle ajustado. En estas situaciones, `CStringT` proporciona un mejor rendimiento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a>Problemas de pérdidas de memoria  
 Pasa la dirección de un inicializado `CComBSTR` a una función como un **[out]** parámetro provoca una pérdida de memoria.  
  
 En el ejemplo siguiente, se asigna la cadena para contener la cadena `"Initialized"` se ha filtrado cuando la función `MyGoodFunction` reemplaza la cadena.  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]  
  
 Para evitar la pérdida, llame a la **vacía** método existente `CComBSTR` objetos antes de pasar la dirección como un **[out]** parámetro.  
  
 Tenga en cuenta que el mismo código no podría causar una pérdida de si el parámetro de la función era **[en, out]**.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [CStringT (clase)](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../standard-library/basic-string-class.md)   
 [Macros de conversión de cadena](../atl/reference/string-conversion-macros.md)

