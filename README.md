CREATE TABLE `User` (
	`id_user` INT(9) NOT NULL,
	`№ fitnes-tracer` INT(15) NOT NULL,
	PRIMARY KEY (`id_user`)
);

CREATE TABLE `data` (
	`id_date` INT(9) NOT NULL,
	`user` INT(15) NOT NULL,
	`activity` INT(5) NOT NULL,
	`pulse` INT(3) NOT NULL,
	`slip` FLOAT(3) NOT NULL,
	`calories` FLOAT(3) NOT NULL,
	PRIMARY KEY (`id_date`)
);

CREATE TABLE `payment` (
	`id_pay` INT(9) NOT NULL,
	`user` INT(15) NOT NULL,
	`accaunt_nomber` INT(16) NOT NULL,
	`period` DATE(8) NOT NULL,
	PRIMARY KEY (`id_pay`)
);

CREATE TABLE `recommendations` (
	`id_recomm` INT(9) NOT NULL,
	`calories` FLOAT(3) NOT NULL,
	`dish` varchar(255) NOT NULL,
	`formula` varchar(255) NOT NULL,
	PRIMARY KEY (`id_recomm`)
);

ALTER TABLE `data` ADD CONSTRAINT `data_fk0` FOREIGN KEY (`user`) REFERENCES `User`(`id_user`);

ALTER TABLE `payment` ADD CONSTRAINT `payment_fk0` FOREIGN KEY (`user`) REFERENCES `User`(`id_user`);

ALTER TABLE `recommendations` ADD CONSTRAINT `recommendations_fk0` FOREIGN KEY (`calories`) REFERENCES `data`(`calories`);
