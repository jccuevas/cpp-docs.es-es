---
title: "Espacios de nombres de plataforma, predeterminado y CLI (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "lang"
  - "cli"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cli (espacio de nombres)"
  - "lang (espacio de nombres)"
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Espacios de nombres de plataforma, predeterminado y CLI (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un espacio de nombres califica los nombres de los elementos de lenguaje de modo que no entren en conflicto con nombres que por lo demás son idénticos en otra parte del código fuente.  Por ejemplo, si se produce una colisión de nombres, es posible que el compilador no reconozca las [Palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  El compilador utiliza los espacios de nombres, pero no se conservan en el ensamblado compilado.  
  
## Todos los runtimes  
 Visual C\+\+ proporciona un espacio de nombres predeterminado para el proyecto cuando se crea.  Puede cambiar manualmente el espacio de nombres, aunque en [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] el nombre del archivo .winmd debe coincidir con el del espacio de nombres de la raíz.  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 Para obtener más información, consulte [Visibilidad de espacios de nombres y tipos \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Sintaxis**  
  
```  
using namespace cli;  
```  
  
 **Comentarios**  
  
 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] admite el espacio de nombres `cli`.  Al compilar con **\/clr**, la instrucción `using` de la sección Sintaxis está implícita.  
  
 Las características de lenguaje siguientes están en el espacio de nombres `cli`:  
  
-   [Matrices](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md)  
  
-   [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se demuestra que se puede usar un símbolo en el espacio de nombres `cli` como símbolo definido por el usuario en el código.  Sin embargo, después de realizar esta acción, deberá calificar explícita o implícitamente las referencias al elemento de lenguaje `cli` del mismo nombre.  
  
```  
// cli_namespace.cpp  
// compile with: /clr  
using namespace cli;  
int main() {  
   array<int> ^ MyArray = gcnew array<int>(100);  
   int array = 0;  
  
   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062  
  
   // OK  
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);  
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);  
}  
```  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)