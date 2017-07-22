# Typescript Decorators

## [Typescript Decorator signatures](http://blog.wolksoftware.com/decorators-reflection-javascript-typescript#decorators-in-typescript_1)

    declare type ClassDecorator = <TFunction extends Function>(target: TFunction) => TFunction | void;
    declare type PropertyDecorator = (target: Object, propertyKey: string | symbol) => void;
    declare type MethodDecorator = <T>(target: Object, propertyKey: string | symbol, descriptor: TypedPropertyDescriptor<T>) => TypedPropertyDescriptor<T> | void;
    declare type ParameterDecorator = (target: Object, propertyKey: string | symbol, parameterIndex: number) => void;

## [Class Decorator](http://blog.wolksoftware.com/decorators-metadata-reflection-in-typescript-from-novice-to-expert-part-ii#2-class-decorator_1)

    function logClass(target: any) {
      // save a reference to the original constructor
      var original = target;
    
      // a utility function to generate instances of a class
      function construct(constructor, args) {
        var c : any = function () {
          return constructor.apply(this, args);
        }
        c.prototype = constructor.prototype;
        return new c();
      }
    
      // the new constructor behaviour
      var f : any = function (...args) {
        console.log("New: " + original.name); 
        return construct(original, args);
      }
    
      // copy prototype so intanceof operator still works
      f.prototype = original.prototype;
    
      // return new constructor (will override original)
      return f;
    }

