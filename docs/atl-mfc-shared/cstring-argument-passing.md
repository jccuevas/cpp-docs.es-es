---
title: Pasar argumentos de CString | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d33c8cc46ada41f851c90aaae0cabfadb1466d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-argument-passing"></a>Paso de argumentos de CString
Este artículo explica cómo pasar [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos a las funciones y cómo devolver `CString` objetos de las funciones.  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a>Convenciones de pasar argumentos de CString  
 Cuando se define una interfaz de clase, debe determinar la convención para pasar argumentos de las funciones de miembro. Hay algunas reglas estándares para pasar y devolver `CString` objetos. Si sigue las reglas descritas en [cadenas como entradas de la función](#_core_strings_as_function_inputs) y [cadenas como resultados de funciones](#_core_strings_as_function_outputs), tendrá el código correcto y eficaz.  
  
##  <a name="_core_strings_as_function_inputs"></a>Cadenas como entradas (función)  
 Una manera más eficaz y segura para utilizar un `CString` objeto en las funciones llamadas consiste en pasar un `CString` objeto a la función. A pesar del nombre, un `CString` objeto no almacena una cadena internamente como una cadena de estilo C que tiene un terminador null. En su lugar, un `CString` objeto mantiene realizar un seguimiento del número de caracteres tiene. Tener `CString` proporcionan un `LPCTSTR` puntero a una cadena terminada en null es una pequeña cantidad de trabajo que puede ser considerable si el código tiene que hacerlo de forma constante. El resultado es temporal porque cualquier cambio en el `CString` contenido invalida copias antiguas de la `LPCTSTR` puntero.  
  
 Tiene sentido en algunos casos, para proporcionar una cadena de estilo C. Por ejemplo, puede haber una situación donde una función llamada está escrita en C y no admite objetos. En este caso, forzar el `CString` parámetro `LPCTSTR`, y la función obtendrá una cadena de estilo C terminada en null. También puede ir a la otra dirección y crear un `CString` objeto mediante el uso de la `CString` constructor que acepta un parámetro de cadena de estilo C.  
  
 Si el contenido de la cadena que deban cambiarse por una función, declare el parámetro como que no es una constante `CString` referencia (**CString &**).  
  
##  <a name="_core_strings_as_function_outputs"></a>Cadenas como resultados de funciones  
 Por lo general puede devolver `CString` objetos de funciones porque `CString` objetos siguen la semántica de valores como tipos primitivos. Para devolver una cadena de solo lectura, utilice una constante `CString` referencia (**const CString &**). En el ejemplo siguiente se muestra el uso de `CString` parámetros y tipos devueltos:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

