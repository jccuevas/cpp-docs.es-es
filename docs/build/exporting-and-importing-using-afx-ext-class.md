---
title: "Exportar e importar mediante AFX_EXT_CLASS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afx_ext_class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX_EXT_CLASS (macro)"
  - "archivos ejecutables [C++], importar clases"
  - "exportar clases [C++]"
  - "exportar DLL [C++], AFX_EXT_CLASS (macro)"
  - "DLL de extensión [C++], exportar clases"
  - "importar archivos DLL [C++]"
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Exportar e importar mediante AFX_EXT_CLASS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[Los archivos DLL de extensión](../build/extension-dlls-overview.md) utilizan la macro **AFX\_EXT\_CLASS** para exportar clases; los archivos ejecutables que se vinculan al archivo DLL de extensión utilizan la macro para importar clases.  Con la macro **AFX\_EXT\_CLASS**, se puede utilizar los mismos archivos de encabezado que para compilar el archivo DLL de extensión con los archivos ejecutables que se vinculan al archivo DLL.  
  
 En el archivo de encabezado para el archivo DLL debe agregar la palabra clave **AFX\_EXT\_CLASS** a la declaración de la clase de la manera siguiente:  
  
```  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
 MFC define esta macro como **\_\_declspec\(dllexport\)** cuando se definen los símbolos de preprocesador **\_AFXDLL** y `_AFXEXT`.  Pero la macro se define como **\_\_declspec\(dllimport\)** cuando **\_AFXDLL** está definido y `_AFXEXT` no está definido.  Cuando está definido, el símbolo de preprocesador **\_AFXDLL** indica que el archivo ejecutable de destino \(un archivo DLL o una aplicación\) está utilizando la versión compartida de MFC.  Si **\_AFXDLL** y `_AFXEXT` están definidos, el archivo ejecutable de destino es un archivo DLL de extensión.  
  
 Como la macro **AFX\_EXT\_CLASS** está definida como **\_\_declspec\(dllexport\)** al exportar desde un archivo DLL de extensión, se pueden exportar clases completas sin colocar los nombres representativos para todos los símbolos de la clase en el archivo .def.  Este método se utiliza en el ejemplo [DLLHUSK](http://msdn.microsoft.com/es-es/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) de MFC.  
  
 Aunque puede evitar la creación de un archivo .def y todos los nombres representativos para la clase con este método, la creación de un archivo .def es más eficaz, ya que se puede exportar los nombres por ordinal.  Para utilizar el método de exportación del archivo .def, coloque el código siguiente al principio y al final del archivo de encabezado:  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  Debe tener cuidado al exportar funciones inline, ya que podrían producir conflictos entre versiones.  Una función inline se expande en el código de la aplicación; por tanto, si después vuelve a escribir la función, no se actualizará a menos que se vuelva a compilar la aplicación.  Normalmente, las funciones de archivos DLL pueden actualizarse sin recompilar las aplicaciones que las utilizan.  
  
## Exportar miembros individuales de una clase  
 Puede que a veces le interese exportar miembros individuales de la clase.  Por ejemplo, si va a exportar una clase derivada de `CDialog`, quizá sólo necesite exportar el constructor y la llamada a `DoModal`.  Puede utilizar **AFX\_EXT\_CLASS** en los miembros individuales que desea exportar.  
  
 Por ejemplo:  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   ...  
   // rest of class definition  
   ...  
};  
```  
  
 Como ya no va a exportar todos los miembros de la clase, podría producirse un problema adicional por la manera en que funcionan las macros de MFC.  Varias macros auxiliares de MFC sirven en realidad para declarar o definir miembros de datos.  Por tanto, también deben exportarse estos miembros de datos desde el archivo DLL.  
  
 Por ejemplo, la macro `DECLARE_DYNAMIC` se define de la manera siguiente cuando se compila un archivo DLL de extensión:  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
 La línea que empieza por static `AFX_DATA` se declara como un objeto estático dentro de la clase.  Para exportar correctamente esta clase y tener acceso a la información en tiempo ejecución desde un archivo ejecutable cliente, deberá exportar este objeto estático.  Como el objeto estático se declara con el modificador `AFX_DATA`, sólo tendrá que definir `AFX_DATA` como **\_\_declspec\(dllexport\)** al compilar el archivo DLL y definirlo como **\_\_declspec\(dllimport\)** al compilar el archivo ejecutable cliente.  Como la macro **AFX\_EXT\_CLASS** ya está definida de esta manera, sólo deberá volver a definir `AFX_DATA` como **AFX\_EXT\_CLASS** en torno a la definición de la clase.  
  
 Por ejemplo:  
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
  
class CExampleView : public CView  
{  
   DECLARE_DYNAMIC()  
   // ... class definition ...  
};  
  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 MFC siempre utiliza el símbolo `AFX_DATA` en los elementos de datos que define dentro de las macros, por lo que esta técnica funcionará para todos estos escenarios.  Por ejemplo, funcionará para `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Si va a exportar toda la clase en lugar de miembros seleccionados de la clase, se exportan automáticamente los miembros de datos estáticos.  
  
### ¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar funciones de C\+\+ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C\+\+](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## Vea también  
 [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)