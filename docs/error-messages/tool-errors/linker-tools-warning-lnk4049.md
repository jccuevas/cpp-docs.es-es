---
title: Las herramientas del vinculador LNK4049 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4049
dev_langs: C++
helpviewer_keywords: LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f44634bd99e485e444ffe9cee7747f31374becf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4049"></a>Advertencia de las herramientas del vinculador LNK4049
el símbolo 'symbol' importado definido localmente  
  
 El símbolo se ha exportado desde tanto importado en el programa.  
  
 Esta advertencia se genera el vinculador cuando se declara un símbolo utilizando el `__declspec(dllexport)` atributo en el archivo de un objeto de clase de almacenamiento y hacer referencia a él mediante el uso de la `__declspec(dllimport)` atributo en otro.  
  
 Advertencia LNK4049 es una versión más general de [Linker Tools Warning LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). El vinculador genera la advertencia LNK4049 cuando no se puede determinar de qué función se hizo referencia al símbolo importado.  
  
 Los casos comunes donde se genera la advertencia LNK4049 en lugar de LNK4217 son:  
  
-   Realizar la vinculación incremental mediante el uso de la [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) opción.  
  
-   Realizando la optimización de todo el programa mediante el uso de la [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opción.  
  
 Para resolver la advertencia LNK4049, pruebe uno de los siguientes:  
  
-   Quitar el `__declspec(dllimport)` el nombre de declaración de la declaración adelantada del símbolo que desencadenó la advertencia LNK4049. Puede buscar símbolos dentro de una imagen binaria mediante el **DUMPBIN** utilidad. El **DUMPBIN/símbolos** conmutador muestra la tabla de símbolos COFF de la imagen. Para obtener más información sobre la **DUMPBIN** utilidad, vea [referencia de DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
-   Deshabilitar temporalmente la vinculación incremental y la optimización de todo el programa. Volver a compilar la aplicación generará la advertencia LNK4217, que incluirá el nombre de la función desde la que se hizo referencia al símbolo importado. Quitar el `__declspec(dllimport)` declaración desde el símbolo importado y habilitar vinculación incremental o la optimización de todo el programa según sea necesario.  
  
 Aunque el código final generado se comportará correctamente, el código generado para llamar a la función importada es menos eficaz que llamar directamente a la función. Esta advertencia no aparecerá cuando se compila con la opción [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Para obtener más información sobre importar y exportar las declaraciones de datos, vea [dllexport, dllimport](../../cpp/dllexport-dllimport.md).  
  
## <a name="example"></a>Ejemplo  
 Vincular los dos módulos siguientes, se generará LNK4049. El primer módulo genera un archivo de objeto que contiene una única función exportada.  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El segundo módulo genera un archivo de objeto que contiene una declaración adelantada a la función exportada en el primer módulo, junto con una llamada a esta función dentro de la `main` (función). Vincular este módulo con el primer módulo generará LNK4049. Quitar el `__declspec(dllimport)` declaración resolverá la advertencia.  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Herramientas del vinculador LNK4217 de advertencia](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)