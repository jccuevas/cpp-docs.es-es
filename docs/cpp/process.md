---
title: proceso | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Process
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d4f2500adaaa7941444b22d7ce548370fc370533
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="process"></a>proceso
Especifica que el proceso de la aplicación administrada debe tener una única copia de una variable global determinada, una variable miembro estática o una variable local estática compartida en todos los dominios de aplicación del proceso. Está diseñado principalmente para usarse cuando se compila con **/CLR: pure**, porque en **/CLR: puro** variables globales y estáticas son por dominio de aplicación, de forma predeterminada. Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015. Cuando se compila con **/CLR**, variables globales y estáticas son por proceso de forma predeterminada (no es necesario usar `__declspec(process)`.  
  
 Solo una variable global, una variable miembro estática o una variable local estática de tipo nativo se pueden marcar con `__declspec(process)`.  
  
 Cuando se compila con **/CLR: pure**, las variables marcadas como por proceso también deben declararse como `const`. De esta manera se garantiza que las variables por proceso no cambian en un dominio de aplicación, lo que puede generar resultados inesperados en otro dominio de aplicación. El uso de previsto principal `__declspec(process)` es habilitar la inicialización en tiempo de compilación de una variable global, una variable miembro estática o una variable local estática en **/CLR: pure**.  
  
 `process`solo es válido cuando se compila con [/CLR](../build/reference/clr-common-language-runtime-compilation.md) o **/CLR: pure** y no es válido cuando se compila con **/CLR: safe**.  
  
 Si desea que cada dominio de aplicación tiene su propia copia de una variable global, utilice [appdomain](../cpp/appdomain.md).  
  
 Vea [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
