- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- -----------------------------------------------------
-- Schema mydb
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema mydb
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `mydb` DEFAULT CHARACTER SET utf8 ;
USE `mydb` ;

-- -----------------------------------------------------
-- Table `mydb`.`Cliente`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Cliente` (
  `idVLiente` INT NOT NULL,
  `Nome` VARCHAR(45) NULL,
  `Identificação` VARCHAR(45) NULL,
  `Endereço` VARCHAR(45) NULL,
  `Tipo de Cliente` VARCHAR(45) NULL,
  PRIMARY KEY (`idVLiente`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Pedido`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Pedido` (
  `idPedido` INT NOT NULL,
  `Status do pedido` VARCHAR(45) NULL,
  `descrição` VARCHAR(45) NULL,
  `Cliente_idVLiente` INT NOT NULL,
  `Frete` FLOAT NULL,
  `Status da entrega` VARCHAR(45) NULL,
  `Codigo de rastreamento` VARCHAR(45) NULL,
  PRIMARY KEY (`idPedido`, `Cliente_idVLiente`),
  INDEX `fk_Pedido_Cliente1_idx` (`Cliente_idVLiente` ASC) VISIBLE,
  CONSTRAINT `fk_Pedido_Cliente1`
    FOREIGN KEY (`Cliente_idVLiente`)
    REFERENCES `mydb`.`Cliente` (`idVLiente`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Produto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Produto` (
  `idProduto` INT NOT NULL,
  `Categoria` VARCHAR(45) NULL,
  `Descrição` VARCHAR(45) NULL,
  `Valor` VARCHAR(45) NULL,
  PRIMARY KEY (`idProduto`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Fornecedor`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Fornecedor` (
  `idFornecedor` INT NOT NULL,
  `Razão Social` VARCHAR(45) NULL,
  `CNPJ` VARCHAR(45) NULL,
  PRIMARY KEY (`idFornecedor`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Disponibilizando um produto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Disponibilizando um produto` (
  `Fornecedor_idFornecedor` INT NOT NULL,
  `Produto_idProduto` INT NOT NULL,
  PRIMARY KEY (`Fornecedor_idFornecedor`, `Produto_idProduto`),
  INDEX `fk_Fornecedor_has_Produto_Produto1_idx` (`Produto_idProduto` ASC) VISIBLE,
  INDEX `fk_Fornecedor_has_Produto_Fornecedor_idx` (`Fornecedor_idFornecedor` ASC) VISIBLE,
  CONSTRAINT `fk_Fornecedor_has_Produto_Fornecedor`
    FOREIGN KEY (`Fornecedor_idFornecedor`)
    REFERENCES `mydb`.`Fornecedor` (`idFornecedor`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Fornecedor_has_Produto_Produto1`
    FOREIGN KEY (`Produto_idProduto`)
    REFERENCES `mydb`.`Produto` (`idProduto`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Estoque`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Estoque` (
  `idEstoque` INT NOT NULL,
  `Local` VARCHAR(45) NULL,
  PRIMARY KEY (`idEstoque`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Produto_has_Estoque`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Produto_has_Estoque` (
  `Produto_idProduto` INT NOT NULL,
  `Estoque_idEstoque` INT NOT NULL,
  `Quantidade` INT NULL,
  PRIMARY KEY (`Produto_idProduto`, `Estoque_idEstoque`),
  INDEX `fk_Produto_has_Estoque_Estoque1_idx` (`Estoque_idEstoque` ASC) VISIBLE,
  INDEX `fk_Produto_has_Estoque_Produto1_idx` (`Produto_idProduto` ASC) VISIBLE,
  CONSTRAINT `fk_Produto_has_Estoque_Produto1`
    FOREIGN KEY (`Produto_idProduto`)
    REFERENCES `mydb`.`Produto` (`idProduto`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Produto_has_Estoque_Estoque1`
    FOREIGN KEY (`Estoque_idEstoque`)
    REFERENCES `mydb`.`Estoque` (`idEstoque`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Relação de Produto/Pedido`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Relação de Produto/Pedido` (
  `Produto_idProduto` INT NOT NULL,
  `Pedido_idPedido` INT NOT NULL,
  `Quantidade do produto` VARCHAR(45) NULL,
  PRIMARY KEY (`Produto_idProduto`, `Pedido_idPedido`),
  INDEX `fk_Produto_has_Pedido_Pedido1_idx` (`Pedido_idPedido` ASC) VISIBLE,
  INDEX `fk_Produto_has_Pedido_Produto1_idx` (`Produto_idProduto` ASC) VISIBLE,
  CONSTRAINT `fk_Produto_has_Pedido_Produto1`
    FOREIGN KEY (`Produto_idProduto`)
    REFERENCES `mydb`.`Produto` (`idProduto`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Produto_has_Pedido_Pedido1`
    FOREIGN KEY (`Pedido_idPedido`)
    REFERENCES `mydb`.`Pedido` (`idPedido`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Terceiro- Vendedor`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Terceiro- Vendedor` (
  `idTerceiro- Vendedor` INT NOT NULL,
  `Razão Social` VARCHAR(45) NULL,
  `Local` VARCHAR(45) NULL,
  PRIMARY KEY (`idTerceiro- Vendedor`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Produtos por Vendedor (terceiros)`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Produtos por Vendedor (terceiros)` (
  `Terceiro- Vendedor_idTerceiro- Vendedor` INT NOT NULL,
  `Produto_idProduto` INT NOT NULL,
  `Quantidade` INT NULL,
  PRIMARY KEY (`Terceiro- Vendedor_idTerceiro- Vendedor`, `Produto_idProduto`),
  INDEX `fk_Terceiro- Vendedor_has_Produto_Produto1_idx` (`Produto_idProduto` ASC) VISIBLE,
  INDEX `fk_Terceiro- Vendedor_has_Produto_Terceiro- Vendedor1_idx` (`Terceiro- Vendedor_idTerceiro- Vendedor` ASC) VISIBLE,
  CONSTRAINT `fk_Terceiro- Vendedor_has_Produto_Terceiro- Vendedor1`
    FOREIGN KEY (`Terceiro- Vendedor_idTerceiro- Vendedor`)
    REFERENCES `mydb`.`Terceiro- Vendedor` (`idTerceiro- Vendedor`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Terceiro- Vendedor_has_Produto_Produto1`
    FOREIGN KEY (`Produto_idProduto`)
    REFERENCES `mydb`.`Produto` (`idProduto`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Cliente_PJ`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Cliente_PJ` (
  `CNPJ` VARCHAR(45) NULL,
  `Razão Social` VARCHAR(45) NULL,
  `Cliente_idVLiente` INT NOT NULL,
  PRIMARY KEY (`Cliente_idVLiente`),
  INDEX `fk_Cliente_PJ_Cliente1_idx` (`Cliente_idVLiente` ASC) VISIBLE,
  CONSTRAINT `fk_Cliente_PJ_Cliente1`
    FOREIGN KEY (`Cliente_idVLiente`)
    REFERENCES `mydb`.`Cliente` (`idVLiente`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Cliente_PF`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Cliente_PF` (
  `CPF` VARCHAR(45) NULL,
  `Razão Social` VARCHAR(45) NULL,
  `Cliente_idVLiente` INT NOT NULL,
  `Data de Nascimento` DATE NULL,
  PRIMARY KEY (`Cliente_idVLiente`),
  INDEX `fk_Cliente_PJ_Cliente1_idx` (`Cliente_idVLiente` ASC) VISIBLE,
  CONSTRAINT `fk_Cliente_PJ_Cliente10`
    FOREIGN KEY (`Cliente_idVLiente`)
    REFERENCES `mydb`.`Cliente` (`idVLiente`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Forma de Pagamento`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Forma de Pagamento` (
  `idForma de Pagamento` INT NOT NULL,
  `Tipo de pagamento` VARCHAR(45) NULL,
  `Numero de Parcelas` VARCHAR(45) NULL,
  `Pedido_idPedido` INT NOT NULL,
  `Pedido_Cliente_idVLiente` INT NOT NULL,
  PRIMARY KEY (`idForma de Pagamento`, `Pedido_idPedido`, `Pedido_Cliente_idVLiente`),
  INDEX `fk_Forma de Pagamento_Pedido1_idx` (`Pedido_idPedido` ASC, `Pedido_Cliente_idVLiente` ASC) VISIBLE,
  CONSTRAINT `fk_Forma de Pagamento_Pedido1`
    FOREIGN KEY (`Pedido_idPedido` , `Pedido_Cliente_idVLiente`)
    REFERENCES `mydb`.`Pedido` (`idPedido` , `Cliente_idVLiente`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Relação Cliente/pagamento`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `mydb`.`Relação Cliente/pagamento` (
  `Cliente_idVLiente` INT NOT NULL,
  `Forma de Pagamento_idForma de Pagamento` INT NOT NULL,
  PRIMARY KEY (`Cliente_idVLiente`, `Forma de Pagamento_idForma de Pagamento`),
  INDEX `fk_Cliente_has_Forma de Pagamento_Forma de Pagamento1_idx` (`Forma de Pagamento_idForma de Pagamento` ASC) VISIBLE,
  INDEX `fk_Cliente_has_Forma de Pagamento_Cliente1_idx` (`Cliente_idVLiente` ASC) VISIBLE,
  CONSTRAINT `fk_Cliente_has_Forma de Pagamento_Cliente1`
    FOREIGN KEY (`Cliente_idVLiente`)
    REFERENCES `mydb`.`Cliente` (`idVLiente`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Cliente_has_Forma de Pagamento_Forma de Pagamento1`
    FOREIGN KEY (`Forma de Pagamento_idForma de Pagamento`)
    REFERENCES `mydb`.`Forma de Pagamento` (`idForma de Pagamento`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
