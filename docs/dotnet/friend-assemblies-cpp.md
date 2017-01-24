---
title: "Ensamblados de confianza (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ensamblados de confianza,Visual C++"
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ensamblados de confianza (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Por runtime aplicables, la característica del lenguaje de ensamblado *de confianza* hace tipos que están en el ámbito de espacio de nombres o el ámbito global en un componente de ensamblado accesible a uno o más ensamblados de cliente o .netmodules.  
  
## Todos los runtimes  
 **Comentarios**  
  
 \(Esta característica de lenguaje no se admite en todos los runtimes.\)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Comentarios**  
  
 \(Esta característica de lenguaje no se admite en [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].\)  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
#### Para hacer que los tipos en el ámbito o el ámbito global del espacio de nombres en un componente de ensamblado accesible para un ensamblado de cliente o un .netmodule  
  
1.  En el componente, especifique un atributo assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, y pase el nombre del ensamblado de cliente o de .netmodule que tendrán acceso a tipos en el ámbito o el ámbito global del espacio de nombres en el componente.  Puede especificar varios ensamblados de cliente o .netmodules especificando atributos adicionales.  
  
2.  En el ensamblado de cliente o el .netmodule, cuando haga referencia al ensamblado de componente mediante `#using`, pase el atributo de `as_friend` .  Si se especifica el atributo de `as_friend` para un ensamblado que no especifique `InternalsVisibleToAttribute`, una excepción en tiempo de ejecución se producirá si intenta tener acceso a un tipo en el ámbito de espacio de nombres o el ámbito global en el componente.  
  
 Un error de compilación se producirá si el ensamblado que contiene el atributo de <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> no tiene un nombre seguro pero el cliente que el ensamblado que utiliza el atributo de `as_friend` .  
  
 Aunque los tipos en el ámbito y el ámbito global del espacio de nombres pueden ser conocidos a un ensamblado de cliente o un .netmodule, la accesibilidad del miembro continúa en vigor.  Por ejemplo, no puede tener acceso a un miembro privado.  
  
 Acceso a todos los tipos en un ensamblado debe explícitamente conceder.  Por ejemplo, el ensamblado C no tiene acceso a todos los ensamblados A los tipos de si el ensamblado c hace referencia al ensamblado b y el ensamblado b tiene acceso a todo el ensamblado. de los tipos.  
  
 Para obtener información sobre cómo especificar la accesibilidad de tipos fuera de un ensamblado, vea [Visibilidad de tipos](../misc/type-visibility.md).  
  
 Para obtener información sobre cómo se signo\- que es, cómo dar un nombre seguro \- uno al ensamblado que se compila con el compilador de Visual C\+\+, vea [Ensamblados de nombre seguro \(Firma de ensamblados\)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
 Como una alternativa a utilizar ensamblados característica, es de confianza puede utilizar <xref:System.Security.Permissions.StrongNameIdentityPermission> para restringir el acceso a los tipos individuales.  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 El ejemplo de código siguiente define un componente que especifica un ensamblado de cliente que tiene acceso a los tipos del componente.  
  
```  
// friend_assemblies.cpp  
// compile by using: /clr /LD  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
[assembly:InternalsVisibleTo("friend_assemblies_2")];  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 El ejemplo de código siguiente tiene acceso a un tipo privado del componente.  
  
```  
// friend_assemblies_2.cpp  
// compile by using: /clr  
#using "friend_assemblies.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
 **Resultados**  
  
 `Class1::Test_Public`  
  
 El ejemplo de código siguiente define un componente pero no especifica un ensamblado de cliente que tiene acceso a los tipos del componente.  
  
 Observe que vinculan al componente mediante **\/opt:noref**.  El garantiza que se emitan a los tipos privados en los metadatos del componente, que no es necesaria si el atributo de `InternalsVisibleTo` está presente.  Para obtener más información, vea [\/OPT \(Optimizaciones\)](../build/reference/opt-optimizations.md).  
  
```  
// friend_assemblies_3.cpp  
// compile by using: /clr /LD /link /opt:noref  
using namespace System;  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 El ejemplo de código siguiente define un cliente que intenta obtener acceso a un private escribir en un componente que no de acceso a los tipos privados.  Debido al comportamiento en tiempo de ejecución, si desea detectar la excepción, debe intentar obtener acceso a un tipo privado en una función auxiliar.  
  
```  
// friend_assemblies_4.cpp  
// compile by using: /clr  
#using "friend_assemblies_3.dll" as_friend  
using namespace System;  
  
void Test() {  
   Class1 ^ a = gcnew Class1;  
}  
  
int main() {  
   // to catch this kind of exception, use a helper function  
   try {  
      Test();     
   }  
   catch(MethodAccessException ^ e) {  
      Console::WriteLine("caught an exception");  
   }  
}  
```  
  
 **Resultados**  
  
 `caught an exception`  
  
 El ejemplo de código siguiente se muestra cómo crear un componente de nombre seguro que especifica un ensamblado de cliente que tiene acceso a los tipos del componente.  
  
```  
// friend_assemblies_5.cpp  
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
  
[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];  
  
private ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 Observe que el componente debe especificar la clave pública.  Recomendamos que ejecute los siguientes comandos secuencialmente en un símbolo del sistema para crear un par de claves y obtener la clave pública:  
  
 **sn \-d friend\_assemblies.snk**  
  
 **sn \-k friend\_assemblies.snk**  
  
 **sn \-i friend\_assemblies.snk friend\_assemblies.snk**  
  
 **sn \-pc friend\_assemblies.snk key.publickey**  
  
 **sn \-tp key.publickey**  
  
 El ejemplo de código siguiente tiene acceso a un tipo privado en el componente de nombre seguro.  
  
```  
// friend_assemblies_6.cpp  
// compile by using: /clr /link /keyfile:friend_assemblies.snk  
#using "friend_assemblies_5.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
 **Resultados**  
  
 `Class1::Test_Public`  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)