# progOrientada
Un velocímetro de un automóvil digital 


import UIKit


enum Velocidades:Int{
    case Apagado = 0, VelocidadBaja = 20, VelocidadMedia = 50, VelocidadAlta = 120
    init(velocidadInicial:Velocidades){
        self = velocidadInicial
    }
    
}

class Auto {
    var velocidad:Velocidades
    init(){
        velocidad = Velocidades(velocidadInicial: .Apagado)
    }
    
    func cambioDeVelocidad() -> ( actual : Int, velocidadEnCadena: String){
        var estado = ""
        let actual = velocidad.rawValue
        switch velocidad {
        case .Apagado:
            velocidad = .VelocidadBaja
            estado = "Apagado"
        case .VelocidadBaja:
            velocidad = .VelocidadMedia
            estado = "Velocidad Baja"
        case .VelocidadMedia:
            velocidad = .VelocidadAlta
            estado = "Velocidad Media"
        case .VelocidadAlta:
            velocidad = .Apagado
            estado = "Velocidad Alta"
        }
        return (actual, estado)
    }
    
}

let auto = Auto()
for i in 1...20 {
    let result = auto.cambioDeVelocidad()
    print("\(i). \(result.actual), \(result.velocidadEnCadena)")
}
