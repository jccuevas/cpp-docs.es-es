---
title: "CType &lt; char &gt; (clase) | Microsoft Docs"
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
  - "ctype<char>"
  - "locale/std::ctype<char>"
  - "std::ctype<char>"
  - "std.ctype<char>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CType < char > (clase)"
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CType &lt; char &gt; (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase es una especialización explícita de la clase de plantilla **ctype \< CharType**> escriba `char`, que describe un objeto que puede actuar como una faceta de configuración regional para caracterizar distintas propiedades de un carácter de tipo `char`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <>  
class ctype<char>  
: public ctype_base  
{  
public:  
    typedef char _Elem;  
    typedef _Elem char_type;  
    bool is(
    mask _Maskval,  
    _Elem _Ch) const;

 
    const _Elem* is(
    const _Elem* first,  
    const _Elem* last,  
    mask* dest) const;

 
    const _Elem* scan_is(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    const _Elem* scan_not(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    _Elem tolower(
    _Elem _Ch) const;

 
    const _Elem* tolower(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem toupper(
    _Elem _Ch) const;

 
    const _Elem* toupper(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem widen(
    char _Byte) const;

 
    const _Elem* widen(
    const char* first,  
    const char* last,  
    _Elem* dest) const;

 
    const _Elem* _Widen_s(
    const char* first,  
    const char* last,  
    _Elem* dest,  
    size_t dest_size) const;

 
    _Elem narrow(
    _Elem _Ch,  
    char _Dflt = '\0') const;

 
    const _Elem* narrow(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest) const;

 
    const _Elem* _Narrow_s(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest,  
    size_t dest_size) const;

 
    static locale::id& id;  
    explicit ctype(
    const mask* _Table = 0,  
    bool _Deletetable = false,  
    size_t _Refs = 0);

protected:  
    virtual ~ctype();
//other protected members  
};  
```  
  
## <a name="remarks"></a>Comentarios  
 La especialización explícita difiere de la clase de plantilla de varias maneras:  
  
-   Un objeto de clase ctype < `char`> almacena un puntero al primer elemento de una tabla de máscara de ctype, una matriz de UCHAR_MAX + 1 elementos del tipo **ctype_base::mask**. También almacena un objeto de tipo Boolean que indica si se debería eliminar la matriz (con `operator delete[]`) cuando el ctype \< **Elem**> se destruye el objeto.  
  
-   Su único constructor público le permite especificar **ficha**, la tabla de máscara ctype, y **SUPR**, el objeto de tipo Boolean que es true si la matriz debe ser eliminado al ctype < `char`> se destruye el objeto, así como el refs de parámetro de recuento de referencias.  
  
-   La función miembro protegida **tabla** devuelve la tabla de máscara de ctype almacenado.  
  
-   El objeto de miembro estático **table_size** especifica el número mínimo de elementos en una tabla de máscara de ctype.  
  
-   La función miembro estática protegida **classic_table**(devuelve la tabla de máscara de ctype apropiado para la configuración regional "C".  
  
-   No hay ninguna función miembro virtual protegida [do_is](../standard-library/ctype-class.md#ctype__do_is), [do_scan_is](../standard-library/ctype-class.md#ctype__do_scan_is), o [do_scan_not](../standard-library/ctype-class.md#ctype__do_scan_not). Las funciones de miembro público correspondiente realizan las operaciones equivalentes a sí mismos.  
  
 Las funciones miembro [do_narrow](../standard-library/ctype-class.md#ctype__do_narrow) y [do_widen](../standard-library/ctype-class.md#ctype__do_widen) Copiar elementos sin modificaciones.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Facet (clase)](../Topic/facet%20Class.md)   
 [ctype_base (clase)](../standard-library/ctype-base-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

