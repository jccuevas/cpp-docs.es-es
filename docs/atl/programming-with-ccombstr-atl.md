---
title: Programar con CComBSTR (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 020c2d18c721e658d15bb1451039154ae50b99f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321794"
---
# <a name="programming-with-ccombstr-atl"></a>Programar con CComBSTR (ATL)

La clase ATL [CComBSTR](../atl/reference/ccombstr-class.md) proporciona un contenedor alrededor del tipo de datos BSTR. Si `CComBSTR` bien es una herramienta útil, hay varias situaciones que requieren precaución.

- [Problemas de conversión](#programmingwithccombstr_conversionissues)

- [Cuestiones de alcance](#programmingwithccombstr_scopeissues)

- [Liberación explícita del objeto CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Uso de objetos CComBSTR en bucles](#programmingwithccombstr_usingloops)

- [Problemas de fuga de memoria](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a>Problemas de conversión

Aunque `CComBSTR` varios métodos convertirán automáticamente un argumento de cadena ANSI en Unicode, los métodos siempre devolverán cadenas de formato Unicode. Para convertir la cadena de salida a ANSI, utilice una clase de conversión ATL. Para obtener más información sobre las clases de conversión ATL, vea Macros de conversión de cadenas [ATL y MFC](reference/string-conversion-macros.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Si utiliza un literal de `CComBSTR` cadena para modificar un objeto, utilice cadenas de caracteres anchos. Esto reducirá las conversiones innecesarias.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a>Cuestiones de alcance

Al igual que con cualquier `CComBSTR` clase que se comporte bien, liberará sus recursos cuando salga del ámbito. Si una función devuelve `CComBSTR` un puntero a la cadena, esto puede causar problemas, ya que el puntero hará referencia a la memoria que ya se ha liberado. En estos casos, `Copy` utilice el método, como se muestra a continuación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a>Liberación explícita del objeto CComBSTR

Es posible liberar explícitamente la cadena `CComBSTR` contenida en el objeto antes de que el objeto salga del ámbito. Si se libera la `CComBSTR` cadena, el objeto no es válido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a>Uso de objetos CComBSTR en bucles

Como `CComBSTR` la clase asigna un búfer para realizar `+=` ciertas operaciones, como el operador o `Append` el método, no se recomienda que realice la manipulación de cadenas dentro de un bucle estrecho. En estas `CStringT` situaciones, proporciona un mejor rendimiento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a>Problemas de fuga de memoria

Pasar la dirección de `CComBSTR` un inicializado a una función como un parámetro **[out]** provoca una pérdida de memoria.

En el ejemplo siguiente, la cadena `"Initialized"` asignada para contener `MyGoodFunction` la cadena se filtra cuando la función reemplaza la cadena.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Para evitar la fuga, llame al `Empty` método en los objetos existentes `CComBSTR` antes de pasar la dirección como un parámetro **[out].**

Tenga en cuenta que el mismo código no provocaría una fuga si el parámetro de la función fuera **[in, out]**.

## <a name="see-also"></a>Consulte también

[Conceptos](../atl/active-template-library-atl-concepts.md)<br/>
[Clase CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Macros de conversión de cadenas](../atl/reference/string-conversion-macros.md)
