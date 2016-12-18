---
title: "Invalidaciones expl&#237;citas (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases derivadas, funciones virtuales"
  - "reemplazo explícito de una función virtual"
  - "invalidaciones explícitas de función virtual"
  - "reemplazar, funciones"
  - "funciones virtuales, reemplazos explícitos"
ms.assetid: ee583234-5cda-4e90-b55e-3f9fbf079ced
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Invalidaciones expl&#237;citas (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Si la misma función virtual se declara en dos o más [interfaces](../cpp/interface.md) y una clase se deriva de estas interfaces, puede invalidar explícitamente cada función virtual.  
  
 Para obtener información sobre las invalidaciones explícitas en código administrado que usan la nueva sintaxis administrada, vea [Invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo utilizar las invalidaciones explícitas:  
  
```  
// deriv_ExplicitOverrides.cpp  
// compile with: /GR  
extern "C" int printf_s(const char *, ...);  
  
__interface IMyInt1 {  
   void mf1();  
   void mf1(int);  
   void mf2();  
   void mf2(int);  
};  
  
__interface IMyInt2 {  
   void mf1();  
   void mf1(int);  
   void mf2();  
   void mf2(int);  
};  
  
class CMyClass : public IMyInt1, public IMyInt2 {  
public:  
   void IMyInt1::mf1() {  
      printf_s("In CMyClass::IMyInt1::mf1()\n");  
   }  
  
   void IMyInt1::mf1(int) {  
      printf_s("In CMyClass::IMyInt1::mf1(int)\n");  
   }  
  
   void IMyInt1::mf2();  
   void IMyInt1::mf2(int);  
  
   void IMyInt2::mf1() {  
      printf_s("In CMyClass::IMyInt2::mf1()\n");  
   }  
  
   void IMyInt2::mf1(int) {  
         printf_s("In CMyClass::IMyInt2::mf1(int)\n");  
   }  
  
   void IMyInt2::mf2();  
   void IMyInt2::mf2(int);  
};  
  
void CMyClass::IMyInt1::mf2() {  
   printf_s("In CMyClass::IMyInt1::mf2()\n");  
}  
  
void CMyClass::IMyInt1::mf2(int) {  
   printf_s("In CMyClass::IMyInt1::mf2(int)\n");  
}  
  
void CMyClass::IMyInt2::mf2() {  
   printf_s("In CMyClass::IMyInt2::mf2()\n");  
}  
  
void CMyClass::IMyInt2::mf2(int) {  
   printf_s("In CMyClass::IMyInt2::mf2(int)\n");  
}  
  
int main() {  
   IMyInt1 *pIMyInt1 = new CMyClass();  
   IMyInt2 *pIMyInt2 = dynamic_cast<IMyInt2 *>(pIMyInt1);  
  
   pIMyInt1->mf1();  
   pIMyInt1->mf1(1);  
   pIMyInt1->mf2();  
   pIMyInt1->mf2(2);  
   pIMyInt2->mf1();  
   pIMyInt2->mf1(3);  
   pIMyInt2->mf2();  
   pIMyInt2->mf2(4);  
  
   // Cast to a CMyClass pointer so that the destructor gets called  
      CMyClass *p = dynamic_cast<CMyClass *>(pIMyInt1);  
      delete p;  
}  
```  
  
  **In CMyClass::IMyInt1::mf1\(\)**  
**In CMyClass::IMyInt1::mf1\(int\)**  
**In CMyClass::IMyInt1::mf2\(\)**  
**In CMyClass::IMyInt1::mf2\(int\)**  
**In CMyClass::IMyInt2::mf1\(\)**  
**In CMyClass::IMyInt2::mf1\(int\)**  
**In CMyClass::IMyInt2::mf2\(\)**  
**In CMyClass::IMyInt2::mf2\(int\)**   
## Vea también  
 [Herencia](../cpp/inheritance-cpp.md)