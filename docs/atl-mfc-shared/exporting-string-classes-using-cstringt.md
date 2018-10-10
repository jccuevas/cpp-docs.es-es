---
title: Exportar clases de cadena mediante CStringT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2d77516ae53b0ee1c4f39e4d8f095848aa00acc
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889976"
---
# <a name="exporting-string-classes-using-cstringt"></a>Exportar clases de cadena mediante CStringT

En el pasado, los desarrolladores de MFC han derivado de `CString` especializar sus propias clases de cadena. En Microsoft Visual C++ .NET (MFC 8.0), el [CString](../atl-mfc-shared/using-cstring.md) clase ha reemplazado por una clase de plantilla denominada [CStringT](../atl-mfc-shared/reference/cstringt-class.md). Esto proporciona varias ventajas:

- Permitía la MFC `CString` proyectos de clase que se utilizará en ATL sin vincular la mayor biblioteca estática de MFC o DLL.

- Con el nuevo `CStringT` clase de plantilla, puede personalizar `CString` comportamiento utilizando los parámetros de plantilla que especifican rasgos de caracteres, similares a las plantillas en la biblioteca estándar de C++.

- Cuando exporta su propia clase de cadena desde un archivo DLL mediante `CStringT`, el compilador también automáticamente exporta el `CString` clase base. Puesto que `CString` es en sí mismo una clase de plantilla, puede crearse por el compilador cuando se utiliza, a menos que el compilador reconoce que `CString` se importa desde un archivo DLL. Si ha migrado proyectos de Visual C++ 6.0 a Visual C++. NET, que puede haber visto errores de símbolo del enlazador para un definido de forma múltiple `CString` debido a la colisión de la `CString` importados desde un archivo DLL y la versión localmente con instancias. A continuación se describe la manera adecuada de hacerlo.

El siguiente escenario hará que el vinculador para generar errores de símbolo para las clases definidos de forma múltiple. Se supone que está exportando un `CString`-clase derivada (`CMyString`) desde un archivo DLL de extensión MFC:

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

El código de consumidor usa una mezcla de `CString` y `CMyString`. "MyString.h" no se incluye en el encabezado precompilado y algo de uso de `CString` no tiene `CMyString` visible.

Supongamos que se usa el `CString` y `CMyString` clases en los archivos de código fuente independiente, Source1.cpp y Source2.cpp. En Source1.cpp, use `CMyString` y #include MyString.h. En Source2.cpp, use `CString`, pero no #include MyString.h. En este caso, el vinculador se quejará sobre `CStringT` que se definió. Esto se debe a `CString` está importado en el archivo DLL que exporta `CMyString`y crea una instancia local por el compilador a través de la `CStringT` plantilla.

Para resolver este problema, realice lo siguiente:

Exportar `CStringA` y `CStringW` (y las clases bases necesarias) desde MFC90. ARCHIVO DLL. Los proyectos que incluyen MFC siempre usará la DLL de MFC exportada `CStringA` y `CStringW`, como en las implementaciones anteriores de MFC.

A continuación, cree una clase derivada puede exportar utilizando el `CStringT` plantilla, como `CStringT_Exported` está por debajo, por ejemplo:

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

En AfxStr.h, reemplace el anterior `CString`, `CStringA`, y `CStringW` typedefs como sigue:

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

Existen algunas advertencias:

- No debe exportar `CStringT` propio porque esto hará que los proyectos de ATL sólo exportar un especializado `CStringT` clase.

- Utilizando un exportable derivado de clase de `CStringT` minimiza la necesidad de volver a implementar `CStringT` funcionalidad. Código adicional se limita a reenviar los constructores para la `CStringT` clase base.

- `CString`, `CStringA`, y `CStringW` solo se debe marcar `__declspec(dllexport/dllimport)` con MFC cuando genera el archivo DLL compartido. Si la vinculación con una biblioteca estática de MFC, no debería marcar estas clases como la exportación; uso de lo contrario, interno de `CString`, `CStringA`, y `CStringW` marcará las DLL de usuario dentro de `CString` como también la exportación.

## <a name="related-topics"></a>Temas relacionados

[CStringT (clase)](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>Vea también

[Uso de CStringT](../atl-mfc-shared/using-cstringt.md)<br/>
[Uso de CString](../atl-mfc-shared/using-cstring.md)

