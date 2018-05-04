---
title: Exportar clases de cadena mediante CStringT | Documentos de Microsoft
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
ms.openlocfilehash: 7510b1f44f49d17211c71419f4dde5a6e6a78974
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-string-classes-using-cstringt"></a>Exportar clases de cadena mediante CStringT
En el pasado, los desarrolladores de MFC se derivan de `CString` especializar sus propias clases de cadena. En Microsoft Visual C++ .NET (versión 8.0 de MFC), el [CString](../atl-mfc-shared/using-cstring.md) clase ha sido reemplazada por una clase de plantilla denominada [CStringT](../atl-mfc-shared/reference/cstringt-class.md). Esto proporciona varias ventajas:  
  
-   Permite la MFC `CString` proyectos de la clase que se utilizará en ATL sin vincular la biblioteca estática MFC o DLL mayor.  
  
-   Con la nueva `CStringT` clase de plantilla, puede personalizar `CString` comportamiento mediante los parámetros de plantilla que especifican rasgos de caracteres, similares a las plantillas en la biblioteca estándar de C++.  
  
-   Cuando exporta su propia clase de cadena de un archivo DLL mediante `CStringT`, el compilador también automáticamente exporta la `CString` clase base. Puesto que `CString` es una clase de plantilla, se pueden crear instancias por el compilador cuando se utiliza, a menos que sea compatible con el compilador que `CString` se importa desde un archivo DLL. Si ha migrado los proyectos de Visual C++ 6.0 a Visual C++. NET, que podría haber visto errores de símbolo del vinculador para un definido de forma múltiple `CString` debido a la colisión de la `CString` importados desde un archivo DLL y la versión local tiene instancia. La manera adecuada para hacer esto se describe a continuación. Para obtener más información sobre este problema, vea el artículo de Knowledge Base, "vinculación errores al importar derivada CString clases" (Q309801) en [ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx).  
  
 El siguiente escenario hará que el vinculador generar errores de símbolo para clases multiplicar definidas. Se supone que va a exportar una `CString`-clase derivada (`CMyString`) desde un archivo DLL de extensión MFC:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]  
  
 El código de consumidor usa una combinación de `CString` y `CMyString`. "MyString.h" no se incluye en el encabezado precompilado y algún uso de `CString` no tiene `CMyString` visible.  
  
 Supongamos que se usa el `CString` y `CMyString` clases en archivos de código fuente independiente, Source1.cpp y Source2.cpp. En Source1.cpp, use `CMyString` y #include MyString.h. En Source2.cpp, utilice `CString`, pero no lo hacen #include MyString.h. En este caso, el vinculador se queja `CStringT` que se definió varias veces. Esto se debe a `CString` está importado en el archivo DLL que exporta `CMyString`y crea una instancia local por el compilador a través de la `CStringT` plantilla.  
  
 Para resolver este problema, haga lo siguiente:  
  
 Exportar `CStringA` y `CStringW` (y las clases base necesarias) desde MFC90. DLL. Proyectos que incluyen MFC siempre utilizarán la DLL de MFC exportada `CStringA` y `CStringW`, como en las implementaciones anteriores de MFC.  
  
 A continuación, cree una clase derivada puede exportar utilizando el `CStringT` plantilla, como `CStringT_Exported` está por debajo, por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]  
  
 En AfxStr.h, reemplace el anterior `CString`, `CStringA`, y `CStringW` definiciones de tipo como se indica a continuación:  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]  
  
 Existen algunas advertencias:  
  
-   No debería exportar `CStringT` propio porque esto hará que sólo ATL proyectos exportar especializada `CStringT` clase.  
  
-   Utilizando un exportable deriva la clase a partir de `CStringT` minimiza la necesidad de volver a implementar `CStringT` funcionalidad. Código adicional se limita al reenvío de constructores para la `CStringT` clase base.  
  
-   `CString`, `CStringA`, y `CStringW` sólo debe marcarse `__declspec(dllexport/dllimport)` cuando se está generando con MFC el archivo DLL compartido. Si vincula a una biblioteca estática de MFC, no debería marcar estas clases como exportarse; uso de lo contrario, es interno de `CString`, `CStringA`, y `CStringW` dentro, se marcarán como usuario dll `CString` como exportarse así.  
  
## <a name="related-topics"></a>Temas relacionados  
 [CStringT (clase)](../atl-mfc-shared/reference/cstringt-class.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de CStringT](../atl-mfc-shared/using-cstringt.md)   
 [Uso de CString](../atl-mfc-shared/using-cstring.md)

