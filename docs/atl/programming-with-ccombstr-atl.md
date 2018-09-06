---
title: Programar con CComBSTR (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 476dd8b3eeb7174c7584a58ccb5d53bf251adbcc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43768013"
---
# <a name="programming-with-ccombstr-atl"></a>Programar con CComBSTR (ATL)

La clase ATL [CComBSTR](../atl/reference/ccombstr-class.md) proporciona un contenedor alrededor del tipo de datos BSTR. Mientras `CComBSTR` es una herramienta útil, hay varias situaciones que requieren precaución.

- [Problemas de conversión](#programmingwithccombstr_conversionissues)

- [Problemas de ámbito](#programmingwithccombstr_scopeissues)

- [Liberar explícitamente el objeto CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Utilizar objetos CComBSTR en bucles](#programmingwithccombstr_usingloops)

- [Problemas de pérdida de memoria](#programmingwithccombstr_memoryleaks)

##  <a name="programmingwithccombstr_conversionissues"></a> Problemas de conversión

Aunque varios `CComBSTR` métodos convertirán automáticamente un argumento de cadena ANSI a Unicode, los métodos siempre devolverá cadenas con formato Unicode. Para convertir la cadena de salida a ANSI, use una clase de conversión de ATL. Para obtener más información sobre las clases de conversión de ATL, vea [Macros de conversión de cadena de MFC y ATL](reference/string-conversion-macros.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Si utilizas un literal de cadena para modificar un `CComBSTR` de objeto, utilice cadenas de caracteres anchos. Esto reducirá las conversiones innecesarias.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

##  <a name="programmingwithccombstr_scopeissues"></a> Problemas de ámbito

Al igual que con cualquier clase y se comporten correctamente, `CComBSTR` libera sus recursos cuando sale de ámbito. Si una función devuelve un puntero a la `CComBSTR` cadena, esto puede causar problemas, como el puntero hará referencia a memoria que ya se ha liberado. En estos casos, utilice el `Copy` método tal y como se muestra a continuación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

##  <a name="programmingwithccombstr_explicitlyfreeing"></a> Liberar explícitamente el objeto CComBSTR

Es posible liberar explícitamente la cadena contenida en el `CComBSTR` antes de que el objeto queda fuera de ámbito de objeto. Si la cadena se libera, el `CComBSTR` objeto no es válido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

##  <a name="programmingwithccombstr_usingloops"></a> Utilizar objetos CComBSTR en bucles

Como el `CComBSTR` clase asigna un búfer para realizar ciertas operaciones, como el `+=` operador o `Append` método, no se recomienda que realice la manipulación de cadenas dentro de un bucle ajustado. En estas situaciones, `CStringT` proporciona un mejor rendimiento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

##  <a name="programmingwithccombstr_memoryleaks"></a> Problemas de pérdida de memoria

Pasa la dirección de inicializada `CComBSTR` a una función como un **[out]** parámetro provoca una pérdida de memoria.

En el ejemplo siguiente, la cadena asignada para contener la cadena `"Initialized"` se pierde cuando la función `MyGoodFunction` reemplaza la cadena.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Para evitar la pérdida, llame el `Empty` método existente `CComBSTR` objetos antes de pasar la dirección como un **[out]** parámetro.

Tenga en cuenta que el mismo código no provocaría una pérdida de si el parámetro de la función era **[en, out]**.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)   
[CStringT (clase)](../atl-mfc-shared/reference/cstringt-class.md)   
[wstring](../standard-library/basic-string-class.md)   
[Macros de conversión de cadena](../atl/reference/string-conversion-macros.md)

