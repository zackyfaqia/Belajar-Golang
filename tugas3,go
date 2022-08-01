package main

import "fmt"

func cariLagu(judul, penyanyi string, T tabPlaylist, n int) bool {
	for i := 0; i <= n; i++ {
		if judul == T[i].lagu.judul && penyanyi == T[i].lagu.penyanyi {
			return true
		}
	}
	return false
}

func buatPlaylist(T *playlist, n int) {
	var (
		judul, penyanyi string
		menit, detik    int
	)
	n = 0
	fmt.Scanln(&judul, &penyanyi)

	for judul != "#" && penyanyi != "#" {
		fmt.Scanln(&menit, &detik)
		if !cariLagu(judul, penyanyi, T, n) {
			T[n].lagu.judul = judul
			T[n].lagu.penyanyi = penyanyi
			T[n].durasi.menit = menit
			T[n].durasi.detik = detik
			n++
		}
		fmt.Scanln(&judul, &penyanyi)
	}
}

func cariTerlama(idx *int, T tabPlaylist, n int) {
	var menit, detik int = 0

	for i := 0; i <= n; i++ {
		if T[i].menit > menit {
			menit = T[i].durasi.menit
			detik = T[i].durasi.detik
			idx = i
		}
	}
}

func cetakPlaylist(T tabPlaylist, n int) {
	var idx int

	cariTerlama(&idx, T, n)
	for i := 0; i <= n; i++ {
		if i == idx {
			fmt.Println("*", T[i].lagu.judul, T[i].durasi.menit, "menit", T[i].durasi.detik, "detik")
		} else {
			fmt.Println(T[i].lagu.judul)
		}
	}
}

const nMax = 1000

type tabPlaylist = [nMax]int
type lagu struct {
	judul, penyanyi string
}
type waktu struct {
	menit, detik int
}
type playlist struct {
	lagu   lagu
	durasi waktu
}

func main() {
	var (
		list tabPlaylist
		n    int
	)
	buatPlaylist(list, n)
	cetakPlaylist(list, n)
}
