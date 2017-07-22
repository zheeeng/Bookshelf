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

## [Method Decorator](http://blog.wolksoftware.com/decorators-metadata-reflection-in-typescript-from-novice-to-expert-part-3#1-parameter-decorators_1)
    
    function logMethod(target: Function, key: string, descriptor: any) {
      var originalMethod = descriptor.value;
      descriptor.value = function (...args: any[]) {
    
        var metadataKey = `__log_${key}_parameters`;
        var indices = target[metadataKey];
    
        if (Array.isArray(indices)) { 
          for (var i = 0; i < args.length; i++) { 
            if (indices.indexOf(i) !== -1) { 
              var arg = args[i];
              var argStr = JSON.stringify(arg) || arg.toString();
              console.log(`${key} arg[${i}]: ${argStr}`);
            }
          }
          var result = originalMethod.apply(this, args);
          return result;
        }
        else {
          var a = args.map(a => (JSON.stringify(a) || a.toString())).join();
          var result = originalMethod.apply(this, args);
          var r = JSON.stringify(result);
          console.log(`Call: ${key}(${a}) => ${r}`);
          return result;
        }
      }
      return descriptor;
    }

